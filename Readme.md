

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
- [Data Types](ddata_types.md)


# 2. Overview of Database Types

A database is an organized collection of information designed to store, manage, and retrieve data efficiently. Different types of databases use different structures and approaches to organize information.

| Database Type | Description | Examples |
|---|---|---|
|  ![Relational (SQL)](/relational.md)  | Stores data in tables consisting of rows and columns, with relationships between tables. | MySQL, PostgreSQL, SQL Server, Oracle |
| **NoSQL** | Stores data in flexible formats, such as documents, key-value pairs, and column-based structures. | MongoDB, Redis, Cassandra |
| **Hierarchical** | Organizes data in a tree structure using parent-child relationships. | IBM IMS |
| **Network** | Organizes data as interconnected records, allowing multiple relationships between records. | Integrated Data Store (IDS) |
| **Object-Oriented** | Stores data as objects, similar to those used in object-oriented programming. | ObjectDB, db4o |
| **Graph** | Represents data using nodes (entities) and edges (relationships). | Neo4j, Amazon Neptune |
| **Time-Series** | Stores timestamped data to support the analysis of changes and trends over time. | InfluxDB, TimescaleDB |

## 2.2 Understanding Relational Databases

A **relational database** is a database management system that organizes information into tables consisting of rows and columns.

These tables can be connected through relationships, allowing information to be stored efficiently, reducing unnecessary data duplication, and making it easier to retrieve related information.

Relational databases are widely used in business applications, financial systems, e-commerce platforms, and information management systems.

### Examples of Relational Database Management Systems (RDBMS)

- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle Database

## 2.3 How Are Relational Databases Organized?

A relational database consists of multiple tables, also known as *relations*. Each table stores information about a particular subject or entity.

For example, an online store might organize its information into separate tables:

- **Customers:** Stores customer information.
- **Products:** Stores product details.
- **Orders:** Stores customer order information.
- **Payments:** Stores payment transactions.

Instead of storing all information in one large table, relational databases separate information into related tables. This approach improves organization and makes data management more efficient.

### Key Components of a Relational Database

| Component | Description |
|---|---|
| **Tables (Relations)** | Structures used to organize and store data. |
| **Rows (Records)** | Individual entries within a table. Each row represents a record. |
| **Columns (Fields)** | Define the attributes or properties of the stored information. |
| **Entities** | Real-world objects or subjects represented in the database, such as customers, products, and orders. |
| **Relationships** | Connections between tables that allow related information to be linked. |

## 2.4 Relationships and Referential Integrity

Relational databases use relationships to connect information stored in different tables.

These relationships help maintain **referential integrity**, which means that references between related records remain valid and consistent.

For example, an order should reference an existing customer rather than a customer who does not exist in the Customers table.

Relationships are commonly established using:

- **Primary Key (PK):** A column or combination of columns that uniquely identifies each record in a table.
- **Foreign Key (FK):** A column or combination of columns that references a key in another table, establishing a relationship between the tables.

## 2.5 Key Takeaways

By the end of this section, students should understand that:

1. Databases come in different types, each designed to organize and manage information differently.
2. Relational databases organize information into tables containing rows and columns.
3. Tables represent different entities, such as customers, products, and orders.
4. Relationships connect tables and allow related information to be retrieved.
5. Primary keys and foreign keys help establish relationships and maintain data integrity.
6. SQL is the language commonly used to communicate with relational databases.



