

# 1. Introduction to Databases

A **database** is a computer application used for storing, managing, and accessing information known as _data_.

Information is entered into a database by an administrator or user and organized into tables. Together, these tables and the information stored in them make up the database.

There are many different types of databases, and they have many uses. For example:

- **Hospitals** use databases to keep track of treatments given to patients.
- **Companies** use databases to store information about their employees.
- **Online stores** use databases to manage customers, products, orders, and payments.

Databases can be simple or very complex, containing many tables that store different types of information. Some databases require **Database Management Systems (DBMS)** to manage and maintain them.

Databases are also useful for research and exploring topics of interest. They allow users to search for specific information, making large amounts of information easier to find, organize, and access.

![DataBases](/img/databases.jpg)

- [Installation](/installation/)
- [Structured Query Language.](/sql/)
- [Data Types](data_types.md)


# 2. Overview of Database Types

A database is an organized collection of information designed to store, manage, and retrieve data efficiently. Different types of databases use different structures and approaches to organize information.

| Database Type | Description | Examples |
|---|---|---|
| [Relational (SQL)](/relational.md)  | Stores data in tables consisting of rows and columns, with relationships between tables. | MySQL, PostgreSQL, SQL Server, Oracle |
| **NoSQL** | Stores data in flexible formats, such as documents, key-value pairs, and column-based structures. | MongoDB, Redis, Cassandra |
| **Hierarchical** | Organizes data in a tree structure using parent-child relationships. | IBM IMS |
| **Network** | Organizes data as interconnected records, allowing multiple relationships between records. | Integrated Data Store (IDS) |
| **Object-Oriented** | Stores data as objects, similar to those used in object-oriented programming. | ObjectDB, db4o |
| **Graph** | Represents data using nodes (entities) and edges (relationships). | Neo4j, Amazon Neptune |
| **Time-Series** | Stores timestamped data to support the analysis of changes and trends over time. | InfluxDB, TimescaleDB |

