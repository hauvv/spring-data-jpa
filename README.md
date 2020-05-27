# GenerationType.IDENTITY
```Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
Hibernate: insert into author (age, genre, name, version) values (?, ?, ?, ?)
2020-05-27 15:13:35.066 DEBUG 27094 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Initiating transaction commit
2020-05-27 15:13:35.066 DEBUG 27094 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Committing JPA transaction on EntityManager [SessionImpl(1778227649<open>)]
2020-05-27 15:13:35.066 DEBUG 27094 --- [           main] o.h.e.t.internal.TransactionImpl         : committing
2020-05-27 15:13:35.069 DEBUG 27094 --- [           main] o.s.orm.jpa.JpaTransactionManager        : Closing JPA EntityManager [SessionImpl(1778227649<open>)] after transaction
2020-05-27 15:13:35.069  INFO 27094 --- [           main] i.StatisticalLoggingSessionEventListener : Session Metrics {
    9131 nanoseconds spent acquiring 1 JDBC connections;
    0 nanoseconds spent releasing 0 JDBC connections;
    111127 nanoseconds spent preparing 9 JDBC statements;
    1895805 nanoseconds spent executing 9 JDBC statements;
    0 nanoseconds spent executing 0 JDBC batches;
    0 nanoseconds spent performing 0 L2C puts;
    0 nanoseconds spent performing 0 L2C hits;
    0 nanoseconds spent performing 0 L2C misses;
    43726 nanoseconds spent executing 1 flushes (flushing a total of 9 entities and 0 collections);
    0 nanoseconds spent executing 0 partial-flushes (flushing a total of 0 entities and 0 collections)
}
Take: 494 ms
```