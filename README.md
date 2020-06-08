# GenerationType in JPA
```$xslt
This project demo how to use GenerationType in JPA to handle batch insert/update
Branch list:
  GenerationType.AUTO
  GenerationType.IDENTITY
  GenerationType.SEQUENCE
  GenerationType.TABLE
  master
1. AUTO & TABLE
Khi để là Auto thì với Hibernate 5, nó sẽ chọn generator là TABLE, khi đó Hibernate sẽ sinh ra 1 bảng để lưu trữ thông tin cho việc generate giá trị cho cột primary key.
a. Nếu hibernate.id.new_generator_mappings=true hoặc k được set thì:
    Hibernate sẽ sinh ra 1 bảng có cấu trúc như sau:
    
    CREATE TABLE `hibernate_sequences` (
        `sequence_name` VARCHAR(255) NOT NULL,
        `next_val` INT(19),
        PRIMARY KEY (`sequence_name`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    Khi chạy code với cấu hình  như này thì việc chạy theo batch sẽ không có tác dụng bởi vì với mỗi bản ghi, 
    Hibernate cần select vào bảng này để lấy và tăng giá trị cho trường ID, cụ thể xem log chạy:
    
    Hibernate: select tbl.next_val from hibernate_sequences tbl where tbl.sequence_name=? for update
    Hibernate: update hibernate_sequences set next_val=?  where next_val=? and sequence_name=?
    Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
    
    Dữ liệu bảng hibernate_sequences như sau:
    
    mysql> select * from hibernate_sequences;
    +---------------+----------+
    | sequence_name | next_val |
    +---------------+----------+
    | default       |     1000 |
    +---------------+----------+
    
b. Nếu hibernate.id.new_generator_mappings=false thì:
    Hibernate sẽ sinh ra 1 bảng có cấu trúc như sau:
    CREATE TABLE `hibernate_sequences` (
        `sequence_name` VARCHAR(255) NOT NULL,
        `sequence_next_hi_value` INT(11),
        PRIMARY KEY (`sequence_name`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    Khi chạy code với cấu hình này, log như sau:
    
    Hibernate: select sequence_next_hi_value from hibernate_sequences where sequence_name = 'author' for update
    Hibernate: update hibernate_sequences set sequence_next_hi_value = ? where sequence_next_hi_value = ? and sequence_name = 'author'
     
    Hibernate sẽ insert vào bảng hibernate_sequences 1 dòng với sequence_name là tên entity và 1 trường sequence_next_hi_value
    mysql> select * from hibernate_sequences;
    +---------------+------------------------+
    | sequence_name | sequence_next_hi_value |
    +---------------+------------------------+
    | author        |                      1 |
    +---------------+------------------------+
    Nếu ta chạy ứng dụng 1 lần  nữa, giá trị sequence_next_hi_value sẽ tăng lên 2, tuy nhiên hãy xem ID của Author:
    mysql> select * from hibernate_sequences;
    +---------------+------------------------+
    | sequence_name | sequence_next_hi_value |
    +---------------+------------------------+
    | author        |                      2 |
    +---------------+------------------------+
    mysql> select * from author;
    +-------+-----+---------+--------+---------+
    | id    | age | genre   | name   | version |
    +-------+-----+---------+--------+---------+
    |     1 |  18 | Genre_0 | Name_0 |       0 |
    | 32768 |  18 | Genre_0 | Name_0 |       0 |
    +-------+-----+---------+--------+---------+
    Tại sao ID của Author lại tăng từ 1 lên 32768?
    Tại vì khi bạn sử dụng cấu hình này, Hibernate sẽ sử dụng thuật toán hi/lo để generate giá trị ID này theo luật như sau:
     - Nếu chưa có dữ liệu trong bảng Author thì sequence_next_hi_value sẽ được set là 1, và id của Author sẽ được set = 1.Sau đó sequence_next_hi_value tăng lên 2
     - Ở lần chạy tiếp theo gía trị của Id Author sẽ là (sequence_next_hi_value-1)*32768 = 1*32768, sequence_next_hi_value tăng lên 3
     - Ở lần chạy thứ 3, giá trị của Id Author sẽ là (sequence_next_hi_value-1)*32768 = 2*32768=65536
     mysql> select * from author;
     +-------+-----+---------+--------+---------+
     | id    | age | genre   | name   | version |
     +-------+-----+---------+--------+---------+
     |     1 |  18 | Genre_0 | Name_0 |       0 |
     | 32768 |  18 | Genre_0 | Name_0 |       0 |
     | 65536 |  18 | Genre_0 | Name_0 |       0 |
     +-------+-----+---------+--------+---------+
     Bản chất thuật toán hi/lo xử lý như sau:
     Thuật toán hi/lo chia sequence domain làm 'hi' nhóm. Giá trị của 'hi' được sinh ra 1 cách đồng bộ. Mỗi 'hi' group được cấp phát tối đa là 'lo' entity
      , và giá trị này có thể được gán 1 cách offline mà k cần lo lắng về lặp giá trị.
      1. Giá trị 'hi' được sinh ra bởi database, 2 tiến trình đồng thời sẽ được gán 2 giá trị khác nhau
      2. Một khi giá trị 'hi' được trả về, chúng ta chỉ cần "incrementSize" để xác định số entity được cấp phát
      3. Giá trị lo được gán theo công thức sau: ((hi -1) * incrementSize) + 1, (hi * incrementSize))   
      4. Khi tất cả các giá trị 'lo' đã được sử dụng, 1 giá trị 'hi' mới sẽ được yêu cầu
     Bạn có thể thay đổi giá trị "incrementSize" bằng cách cấu hình:
     @Id
     @TableGenerator(
         name = "clazz_gen", 
         table = "id_gen", 
         pkColumnName = "gen_name", 
         valueColumnName = "gen_val", 
         allocationSize = 1
     )
     @GeneratedValue(strategy = GenerationType.TABLE, generator = "clazz_gen")
     private Long id;
 2. IDENTITY
    Đây là cấu hình thuật tiện nhất. Khi sử dụng cấu hình này, Hibernate sẽ tận dụng việc hỗ trợ trường "AUTO_INCREMENT" của Database, khi đó ứng dụng k cần
    quan tâm đến việc set giá trị của trường primary key nữa, mà việc này Database sẽ đảm nhiệm (bản chất DB khi đó sẽ tự động gen trường này khi insert vào table, mà app k cần gọi thêm câu lệnh nào)
    --> Recomend sử dụng cấu hình này với stack : MySql, Hibernate 5
 3. SEQUENCE
    Khi sử dụng cấu hình này, Hibernate sẽ sử dụng 1 bảng hibernate_sequence (lưu ý là k có 's' như cấu hình AUTO & TABLE), và bảng này sẽ có cấu trúc như sau:
    CREATE TABLE `hibernate_sequence` (
        `next_val` INT(19),
        PRIMARY KEY (`sequence_name`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    Tất cả các Entity đều sử dụng chung 1 bảng để quản lý next_val. Để chỉ định riêng mỗi Entity một next_val thì chúng ta cần tạo thủ công bảng hibernate_sequence với cấu trúc như sau:
    CREATE TABLE `hibernate_sequence` (
        `sequence_name` VARCHAR(255) NOT NULL,
        `next_val` INT(19),
        PRIMARY KEY (`sequence_name`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    và Insert giá trị ban đầu cho entity:
    INSERT INTO hibernate_sequence SET sequence_name='Author', next_val=1;
    Khi đó mỗi Entity sẽ được quản lý next_val như 1 bản ghi trong bản này với sequence_name là tên Entity
    mysql> select * from hibernate_sequence;
    +---------------+----------+
    | sequence_name | next_val |
    +---------------+----------+
    | Author        |        2 |
    +---------------+----------+

Recommended to use: GenerationType.IDENTITY with MySql & hibernate 5 tech stack

Link:
 - https://dzone.com/articles/50-best-performance-practices-for-hibernate-5-amp
 - https://vladmihalcea.com/why-should-not-use-the-auto-jpa-generationtype-with-mysql-and-hibernate/
 - https://vladmihalcea.com/why-you-should-never-use-the-table-identifier-generator-with-jpa-and-hibernate/
 - https://vladmihalcea.com/how-to-replace-the-table-identifier-generator-with-either-sequence-or-identity-in-a-portable-way/
 - https://vladmihalcea.com/the-hilo-algorithm/
```