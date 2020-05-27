# GenerationType in JPA
```$xslt
This project demo how to use GenerationType in JPA to handle batch insert/update
Branch list:
  GenerationType.AUTO
  GenerationType.IDENTITY
  GenerationType.SEQUENCE
  master

Why not using AUTO?
GenerationType.AUTO is not a good pick for MySQL since, from Hibernate 5, it falls back to TABLE generator, which is bad for performance.

Recommended to use: GenerationType.IDENTITY

Link:
 - https://dzone.com/articles/50-best-performance-practices-for-hibernate-5-amp
 - https://vladmihalcea.com/why-should-not-use-the-auto-jpa-generationtype-with-mysql-and-hibernate/
 - https://vladmihalcea.com/why-you-should-never-use-the-table-identifier-generator-with-jpa-and-hibernate/
 - https://vladmihalcea.com/how-to-replace-the-table-identifier-generator-with-either-sequence-or-identity-in-a-portable-way/
 - https://vladmihalcea.com/the-hilo-algorithm/
```