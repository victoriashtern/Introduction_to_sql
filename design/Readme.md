# Database Terminology Glossary

| Attribute | Description |
|---|---|
| **Boyce-Codd Normal Form (BCNF)** | A higher level of database normalization in which every determinant must be a candidate key. It helps eliminate data redundancy and update anomalies. |
| **Candidate Key** | A column or combination of columns that can uniquely identify each record in a table. A table can have multiple candidate keys. |
| **Concatenation** | The process of combining two or more strings or values into a single string or value. |
| **Database Design** | The process of planning and organizing a database, including its tables, fields, relationships, and constraints. |
| **Database Management System (DBMS)** | Software used to create, store, manage, retrieve, and manipulate data in a database. Examples include MySQL, PostgreSQL, and SQL Server. |
| **Determinant** | An attribute or combination of attributes that determines the value of another attribute through a functional dependency. |
| **Entity** | A person, place, object, event, or concept about which data is stored. For example, a Student or Course. |
| **Entity-Relationship (E-R) Diagram** | A visual representation of entities, their attributes, and the relationships between them in a database. |
| **Field** | A single attribute or column in a database table that stores a particular type of information. |
| **First Normal Form (1NF)** | A table is in 1NF when each field contains a single, atomic value and there are no repeating groups. |
| **Functionally Dependent** | An attribute is functionally dependent on another attribute when the value of the first attribute is uniquely determined by the value of the second. |
| **Functionally Determine** | An attribute or set of attributes functionally determines another attribute when each value of the first uniquely identifies one value of the second. |
| **Nonkey Column** | A column that is not part of a candidate key in a relational database table. |
| **Normal Form** | A set of rules or standards that a database table must satisfy to meet a particular level of normalization. |
| **Normalization** | The process of organizing database tables to reduce data redundancy and prevent data anomalies. |
| **One-to-Many Relationship** | A relationship in which one record in a table can be associated with multiple records in another table. For example, one customer can place many orders. |
| **Primary Key** | A column or combination of columns that uniquely identifies each record in a table. Primary key values cannot be NULL or duplicated. |
| **Qualify** | To meet a particular condition or requirement. In databases, an attribute qualifies as a key when it satisfies the required uniqueness and identification rules. |
| **Record** | A collection of related fields representing one instance of an entity. A record is also called a row or tuple. |
| **Redundancy** | The unnecessary duplication of data in a database, which can lead to wasted storage and data inconsistencies. |
| **Relation** | A table in a relational database consisting of rows and columns. |
| **Relational Database** | A database that organizes data into related tables consisting of rows and columns. Tables are connected using keys. |
| **Relationship** | An association between two or more entities or tables in a database. |
| **Repeating Group** | A set of multiple values or attributes repeated within a single record, rather than being stored in separate rows. Repeating groups violate 1NF. |
| **Second Normal Form (2NF)** | A table is in 2NF when it is in 1NF and every nonkey column is fully functionally dependent on the entire candidate key, with no partial dependencies. |
| **Third Normal Form (3NF)** | A table is in 3NF when it is in 2NF and has no transitive dependencies of nonkey columns on candidate keys. |
| **Tuple** | A single row in a relational database table. It represents one record in a relation. |
| **Unnormalized Relation** | A table or relation that has not yet been organized according to normalization rules and may contain repeating groups or duplicated data. |
| **Update Anomaly** | A data inconsistency problem that occurs when the same information is stored in multiple places and an update is not applied to every occurrence. |
```

Note: In relational database terminology, a relation is a table, a tuple is a row, and an attribute is a column. These terms are often used interchangeably with table, record, and field in introductory database courses.
