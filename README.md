# spring-data-jpa
```$xslt
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
2020-05-27 15:32:42.338 DEBUG 28443 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Initiating transaction commit
2020-05-27 15:32:42.339 DEBUG 28443 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Committing JPA transaction on EntityManager [SessionImpl(1651372403<open>)]
2020-05-27 15:32:42.339 DEBUG 28443 --- [           main] o.h.e.t.internal.TransactionImpl         : committing
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
2020-05-27 15:32:42.346 DEBUG 28443 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Closing JPA EntityManager [SessionImpl(1651372403<open>)] after transaction
2020-05-27 15:32:42.346  INFO 28443 --- [           main] i.StatisticalLoggingSessionEventListener : Session Metrics {
    123011 nanoseconds spent acquiring 31 JDBC connections;
    158176 nanoseconds spent releasing 30 JDBC connections;
    581862 nanoseconds spent preparing 61 JDBC statements;
    35583523 nanoseconds spent executing 60 JDBC statements;
    3206334 nanoseconds spent executing 1 JDBC batches;
    0 nanoseconds spent performing 0 L2C puts;
    0 nanoseconds spent performing 0 L2C hits;
    0 nanoseconds spent performing 0 L2C misses;
    4493502 nanoseconds spent executing 1 flushes (flushing a total of 30 entities and 0 collections);
    0 nanoseconds spent executing 0 partial-flushes (flushing a total of 0 entities and 0 collections)
}
Take: 4636 ms
```