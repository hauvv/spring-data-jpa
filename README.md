#  GenerationType.AUTO
```$xslt
When you use the GenerationType.AUTO:
In older versions, Hibernate selected the GenerationType.IDENTITY for MySQL databases. 
That was a good choice. As explained earlier, it’s the most efficient approach available.
But that changed in Hibernate 5. It now selects the GenerationType.TABLE which uses a database table to generate primary keys. 
This approach requires a lot of database queries and pessimistic locks to generate unique values.

Hibernate: drop table if exists author
Hibernate: drop table if exists hibernate_sequence
Hibernate: create table author (id bigint not null, age integer not null, genre varchar(255), name varchar(255), version smallint, primary key (id)) engine=InnoDB
Hibernate: create table hibernate_sequence (next_val bigint) engine=InnoDB
Hibernate: insert into hibernate_sequence values ( 1 )

Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
Hibernate: select next_val as id_val from hibernate_sequence for update
Hibernate: update hibernate_sequence set next_val= ? where next_val=?
2020-05-27 15:43:49.961 DEBUG 29318 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Initiating transaction commit
2020-05-27 15:43:49.961 DEBUG 29318 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Committing JPA transaction on EntityManager [SessionImpl(2130299045<open>)]
2020-05-27 15:43:49.961 DEBUG 29318 --- [           main] o.h.e.t.internal.TransactionImpl         : committing
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version, id) values (?, ?, ?, ?, ?)
2020-05-27 15:43:49.973 DEBUG 29318 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Closing JPA EntityManager [SessionImpl(2130299045<open>)] after transaction
2020-05-27 15:43:49.974  INFO 29318 --- [           main] i.StatisticalLoggingSessionEventListener : Session Metrics {
    93969 nanoseconds spent acquiring 31 JDBC connections;
    92321 nanoseconds spent releasing 30 JDBC connections;
    524395 nanoseconds spent preparing 61 JDBC statements;
    41711065 nanoseconds spent executing 60 JDBC statements;
    6242931 nanoseconds spent executing 1 JDBC batches;
    0 nanoseconds spent performing 0 L2C puts;
    0 nanoseconds spent performing 0 L2C hits;
    0 nanoseconds spent performing 0 L2C misses;
    8728891 nanoseconds spent executing 1 flushes (flushing a total of 30 entities and 0 collections);
    0 nanoseconds spent executing 0 partial-flushes (flushing a total of 0 entities and 0 collections)
}
Take: 5214 ms


--> How to fix:
@Id
    @GeneratedValue(
            strategy= GenerationType.AUTO,
            generator="native"
    )
    @GenericGenerator(
            name = "native",
            strategy = "native"
    )
    private Long id;
```