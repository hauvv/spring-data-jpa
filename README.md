# spring-data-jpa
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
```