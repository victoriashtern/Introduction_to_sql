Here is the Markdown (`.md`) version, ready to copy into a file such as `mysql-data-types.md`.

Writing

# MySQL Data Types – Complete Reference Guide

MySQL data types determine the kind of values that can be stored in a table column. Choosing the appropriate data type is an essential part of database design, as it affects data accuracy, storage efficiency, performance, and the overall integrity of your database.

MySQL provides a comprehensive collection of data types for handling different kinds of information, including numeric values, strings, dates and times, binary data, JSON documents, and geographical information.

This guide provides a structured reference to MySQL's built-in data types, their characteristics, practical applications, and recommendations for choosing the right type when designing database schemas.

\!MySQL Data Types

---

## Table of Contents

1. Numeric Data Types
2. String and Text Data Types
3. Date and Time Data Types
4. JSON Data Type
5. Spatial (GIS) Data Types
6. Common MySQL Type Aliases
7. Choosing the Right Data Type
8. Complete CREATE TABLE Example
9. Quick Reference Guide
10. Best Practices and Recommendations

---

## 1\. Numeric Data Types

Numeric data types are used to store numerical values, including integers, exact decimal numbers, and approximate floating-point values.

MySQL provides several numeric types, each designed for different storage requirements and levels of precision.

### Numeric Data Types Reference

| Data Type | Storage | Signed Range | Unsigned Range | Typical Use |
| --- | --- | --- | --- | --- |
| TINYINT | 1 byte | -128 to 127 | 0 to 255 | Age, flags, status |
| SMALLINT | 2 bytes | -32,768 to 32,767 | 0 to 65,535 | Small quantities |
| MEDIUMINT | 3 bytes | -8,388,608 to 8,388,607 | 0 to 16,777,215 | Medium-sized counters |
| INT / INTEGER | 4 bytes | -2,147,483,648 to 2,147,483,647 | 0 to 4,294,967,295 | IDs, quantities |
| BIGINT | 8 bytes | Approximately ±9.22 × 10¹⁸ | 0 to 1.84 × 10¹⁹ | Large identifiers, counters |
| DECIMAL(p,s) | Variable | Depends on precision | Depends on precision | Prices, financial values |
| NUMERIC(p,s) | Variable | Depends on precision | Depends on precision | Exact decimal values |
| FLOAT | 4 bytes | Approx. ±3.4 × 10³⁸ | N/A | Scientific calculations |
| DOUBLE | 8 bytes | Approx. ±1.8 × 10³⁰⁸ | N/A | Measurements, calculations |
| BIT(n) | Up to 64 bits | N/A | 0 to 2ⁿ - 1 | Bit fields |
| BOOLEAN | 1 byte | Commonly 0 or 1 | N/A | True/false values |
| BOOL | 1 byte | Commonly 0 or 1 | N/A | True/false values |

### Understanding Numeric Types

**Integer Types**

Integer types store whole numbers without decimal places.

- `TINYINT`: Suitable for small numerical values, such as ages and status codes.
- `SMALLINT`: Appropriate for relatively small quantities.
- `MEDIUMINT`: Useful when a value exceeds the range of SMALLINT.
- `INT`: A common choice for identifiers, quantities, and general-purpose numerical values.
- `BIGINT`: Designed for very large integers, such as high-volume counters and identifiers.

**Exact Decimal Types**

`DECIMAL(p,s)` stores numbers with exact decimal precision.

- `p` represents the total number of digits.
- `s` represents the number of digits after the decimal point.

For example:

sql

```sql
DECIMAL(10,2)
```

Allows up to 10 digits in total, with 2 digits after the decimal point.

This makes DECIMAL particularly suitable for financial calculations, prices, and monetary values.

**Floating-Point Types**

- `FLOAT` stores approximate numerical values using single precision.
- `DOUBLE` stores approximate numerical values using double precision.

These types are appropriate for scientific calculations and measurements where approximate precision is acceptable.

Avoid using FLOAT and DOUBLE for financial calculations because they cannot represent every decimal value exactly.

**Additional Notes**

- `UNSIGNED` removes the negative range for supported integer types.
- `BIT(n)` supports between 1 and 64 bits.
- `BOOLEAN` and `BOOL` are aliases for `TINYINT(1)`.
- MySQL commonly represents FALSE as `0` and TRUE as `1`, but BOOLEAN does not restrict a column to only those two values.
- BIGINT ranges are rounded for readability.

### Example

sql

```sql
CREATE TABLE products (
    id INT UNSIGNED,
    quantity SMALLINT UNSIGNED,
    price DECIMAL(10,2),
    discount FLOAT
);
```

---

## 2\. String and Text Data Types

String data types store textual information, characters, and binary values.

MySQL provides fixed-length strings, variable-length strings, large text fields, binary storage types, and predefined-value types.

### String and Text Data Types Reference

| Data Type | Maximum Size | Description | Typical Use |
| --- | --- | --- | --- |
| CHAR(n) | 255 characters | Fixed-length string | Country codes, fixed identifiers |
| VARCHAR(n) | 65,535 bytes (row-dependent) | Variable-length string | Names, emails, addresses |
| BINARY(n) | 255 bytes | Fixed-length binary data | Binary identifiers |
| VARBINARY(n) | 65,535 bytes (row-dependent) | Variable-length binary data | Binary values |
| TINYTEXT | 255 bytes | Very short text | Short descriptions |
| TEXT | 65,535 bytes | Standard text | Comments, descriptions |
| MEDIUMTEXT | 16,777,215 bytes | Medium-sized text | Articles, documents |
| LONGTEXT | 4,294,967,295 bytes | Very large text | Large text content |
| TINYBLOB | 255 bytes | Small binary data | Small binary files |
| BLOB | 65,535 bytes | Binary data | Images, files |
| MEDIUMBLOB | 16,777,215 bytes | Medium binary data | Medium-sized files |
| LONGBLOB | 4,294,967,295 bytes | Large binary data | Large binary files |
| ENUM | Up to 65,535 members | One value from a predefined list | Status, categories |
| SET | Up to 64 members | Zero or more predefined values | Multiple permissions |

_Note: String and binary storage limits are expressed in bytes where applicable. Actual VARCHAR capacity depends on row size, character set, and other columns._

### Understanding String Types

**Fixed-Length and Variable-Length Strings**

- `CHAR(n)` reserves a fixed-length string and is useful for values with consistent lengths.
- `VARCHAR(n)` stores variable-length strings and is generally preferred for names, email addresses, and other text fields with varying lengths.

**Text Types**

MySQL provides four TEXT variants:

- `TINYTEXT`: For very short text.
- `TEXT`: For standard descriptions and comments.
- `MEDIUMTEXT`: For larger documents and articles.
- `LONGTEXT`: For very large text content.

**Binary Types**

Binary types store data as bytes rather than character-based text.

- `BINARY` and `VARBINARY` store fixed-length and variable-length binary values.
- `BLOB` types are designed for larger binary objects, such as images and files.

**ENUM and SET**

- `ENUM` restricts a column to one value from a predefined collection.
- `SET` allows a column to contain zero or more values from a predefined collection.

### Example

sql

```sql
CREATE TABLE customers (
    id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    country_code CHAR(2),
    email VARCHAR(255),
    biography TEXT,
    status ENUM('ACTIVE', 'INACTIVE', 'PENDING')
);
```

---

## 3\. Date and Time Data Types

Date and time data types store calendar dates, time values, and timestamps.

They are commonly used for recording birthdays, appointments, transactions, registration dates, and record creation or modification times.

### Date and Time Data Types Reference

| Data Type | Storage | Range | Description | Typical Use |
| --- | --- | --- | --- | --- |
| DATE | 3 bytes | 1000-01-01 to 9999-12-31 | Stores a calendar date | Birthdays, registration dates |
| TIME | 3 bytes (+ fractional seconds) | -838:59:59 to 838:59:59 | Stores time or duration | Opening times, durations |
| DATETIME | 5 bytes (+ fractional seconds) | 1000-01-01 to 9999-12-31 | Stores date and time | Orders, appointments |
| TIMESTAMP | 4 bytes (+ fractional seconds) | Approximately 1970-01-01 to 2038-01-19 | Stores date and time with timezone conversion | Creation and update times |
| YEAR | 1 byte | 1901 to 2155, or 0000 | Stores a year | Manufacturing year |

### Fractional Seconds Precision

MySQL supports fractional seconds precision from 0 to 6 digits.

This allows date and time values to include fractions of a second.

Examples:

- `TIME(3)`: Millisecond precision.
- `DATETIME(6)`: Microsecond precision.
- `TIMESTAMP(6)`: Microsecond precision.

### Understanding Date and Time Types

- `DATE`: Stores a date without a time component.
- `TIME`: Stores a time value or a positive or negative duration.
- `DATETIME`: Stores both date and time without automatic timezone conversion.
- `TIMESTAMP`: Converts values between the session timezone and UTC.
- `YEAR`: Stores a year value.

**Important considerations:**

- DATETIME supports a wider date range than TIMESTAMP.
- TIMESTAMP is useful for automatically managed creation and modification times.
- DATETIME is appropriate when you need to preserve a date and time without automatic timezone conversion.

### Example

sql

```sql
CREATE TABLE appointments (
    id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    appointment_date DATE,
    appointment_time TIME,
    appointment_datetime DATETIME,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 4\. JSON Data Type

The JSON data type allows MySQL to store structured JSON documents directly in a table column.

It is particularly useful when working with APIs, flexible application attributes, configuration settings, and semi-structured information.

### JSON Data Type Reference

| Data Type | Description | Example | Typical Use |
| --- | --- | --- | --- |
| JSON | Stores validated JSON documents | {"name":"John","age":25} | API data, flexible attributes |

### Working with JSON

MySQL validates JSON documents when they are inserted or updated.

JSON supports several value types:

- Objects
- Arrays
- Strings
- Numbers
- Boolean values
- Null values

MySQL also provides JSON functions and operators for extracting, searching, modifying, and manipulating JSON documents.

### Example

sql

```sql
CREATE TABLE users (
    id INT,
    details JSON
);

INSERT INTO users VALUES (
    1,
    '{"name":"John","age":25}'
);

SELECT details->>'$.name'
FROM users;
```

### Important Notes

- JSON columns automatically validate JSON documents.
- JSON values can be queried using JSON functions and operators.
- JSON columns cannot be indexed directly like ordinary scalar columns.
- Generated columns and multi-valued indexes can be used to index appropriate JSON values.

---

## 5\. Spatial (GIS) Data Types

MySQL provides spatial data types for storing geographical and geometric information.

These types are useful for applications involving maps, geographical coordinates, routes, boundaries, and location-based services.

### Spatial Data Types Reference

| Data Type | Description | Typical Use |
| --- | --- | --- |
| GEOMETRY | Represents any geometry type | General spatial information |
| POINT | Represents a single point | GPS coordinates, locations |
| LINESTRING | Represents a sequence of connected points | Roads, routes |
| POLYGON | Represents an enclosed area | Property boundaries |
| MULTIPOINT | Represents multiple points | Multiple locations |
| MULTILINESTRING | Represents multiple line strings | Road networks |
| MULTIPOLYGON | Represents multiple polygons | Geographic regions |
| GEOMETRYCOLLECTION | Represents a collection of different geometries | Complex geographic data |

### Understanding Spatial Types

- `POINT`: Represents a single location using coordinates.
- `LINESTRING`: Represents a connected sequence of points.
- `POLYGON`: Represents a closed geographical area.
- `MULTIPOINT`: Contains multiple points.
- `MULTILINESTRING`: Contains multiple line strings.
- `MULTIPOLYGON`: Contains multiple polygons.
- `GEOMETRYCOLLECTION`: Combines different geometry types.

### Example

sql

```sql
CREATE TABLE locations (
    id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    coordinates POINT NOT NULL,
    SPATIAL INDEX (coordinates)
);
```

---

## 6\. Common MySQL Type Aliases

MySQL supports several alternative names for existing data types.

These aliases provide additional flexibility when defining database columns, although they do not necessarily introduce different storage behavior.

### Type Aliases Reference

| Alias | Equivalent Type | Example |
| --- | --- | --- |
| INTEGER | INT | INTEGER |
| BOOL | TINYINT | BOOL |
| BOOLEAN | TINYINT | BOOLEAN |
| NUMERIC | DECIMAL | NUMERIC(10,2) |
| DEC | DECIMAL | DEC(10,2) |
| FIXED | DECIMAL | FIXED(10,2) |
| REAL | Usually DOUBLE | REAL |
| DOUBLE PRECISION | DOUBLE | DOUBLE PRECISION |

**Important:** REAL normally behaves as DOUBLE, but its behavior can change when the `REAL_AS_FLOAT` SQL mode is enabled.

---

## 7\. Choosing the Right Data Type

Selecting the appropriate data type is an important step in database design.

The choice should reflect the nature of the information being stored, the expected value range, precision requirements, and future application needs.

### Practical Data Type Selection

| Database Field | Recommended Type | Example Value | Reason |
| --- | --- | --- | --- |
| User ID | BIGINT UNSIGNED | 100001 | Supports large identifiers |
| First name | VARCHAR(100) | John | Variable-length text |
| Last name | VARCHAR(100) | Smith | Variable-length text |
| Email | VARCHAR(255) | john@email.com | Email address |
| Password hash | VARCHAR(255) | a8f5f167... | Stores password hashes |
| Age | TINYINT UNSIGNED | 25 | Small positive integer |
| Price | DECIMAL(10,2) | 199.99 | Exact monetary value |
| Quantity | INT UNSIGNED | 500 | Whole-number quantity |
| Discount | DECIMAL(5,2) | 15.50 | Precise percentage |
| Is active | BOOLEAN | TRUE | Boolean-style value |
| Description | TEXT | Product description... | Longer text |
| Profile image | BLOB | Binary image data | Binary storage |
| Birth date | DATE | 1995-05-20 | Date without time |
| Created date | TIMESTAMP | 2026-11-12 15:30:00 | Record creation time |
| Appointment | DATETIME | 2026-11-15 10:30:00 | Date and time |
| User preferences | JSON | {"theme":"dark"} | Flexible structured data |

_Design consideration: Passwords should never be stored as plain text. Store securely generated password hashes instead. Also, consider storing large images and files in external object storage when appropriate._

---

## 8\. Complete CREATE TABLE Example

The following example demonstrates how different MySQL data types can be combined to create a practical database table.

It includes identifiers, strings, numeric values, predefined choices, dates, timestamps, text, and JSON data.

### Employee Table

sql

```sql
CREATE TABLE employees (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,

    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,

    email VARCHAR(255) UNIQUE,

    age TINYINT UNSIGNED,

    salary DECIMAL(10,2),

    is_active BOOLEAN DEFAULT TRUE,

    department ENUM(
        'IT',
        'HR',
        'SALES',
        'FINANCE'
    ),

    description TEXT,

    birth_date DATE,

    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        ON UPDATE CURRENT_TIMESTAMP,

    preferences JSON
);
```

### What This Example Demonstrates

- `BIGINT UNSIGNED`: Stores employee identifiers.
- `VARCHAR`: Stores employee names and email addresses.
- `TINYINT UNSIGNED`: Stores a positive age value.
- `DECIMAL`: Stores salary values with exact decimal precision.
- `BOOLEAN`: Represents an active or inactive status.
- `ENUM`: Restricts the department to predefined choices.
- `TEXT`: Stores longer employee descriptions.
- `DATE`: Stores the employee's birth date.
- `TIMESTAMP`: Automatically manages creation and modification times.
- `JSON`: Stores flexible employee preferences.

---

## 9\. Quick Reference Guide

Use the following table as a quick reference when selecting a MySQL data type.

| If You Need to Store... | Recommended Type |
| --- | --- |
| Small whole numbers | TINYINT |
| Medium-sized whole numbers | SMALLINT / MEDIUMINT |
| Standard whole numbers | INT |
| Very large whole numbers | BIGINT |
| Monetary values | DECIMAL |
| Approximate decimal values | FLOAT / DOUBLE |
| Short variable-length text | VARCHAR |
| Fixed-length text | CHAR |
| Long text | TEXT |
| Very large text documents | LONGTEXT |
| Binary files | BLOB |
| Calendar dates | DATE |
| Time values or durations | TIME |
| Date and time | DATETIME |
| Automatically managed timestamps | TIMESTAMP |
| Boolean-style values | BOOLEAN |
| Structured JSON documents | JSON |
| Geographical coordinates | POINT |
| A single predefined choice | ENUM |
| Multiple predefined choices | SET |

---

## 10\. Best Practices and Recommendations

Choosing the right MySQL data type helps maintain data consistency, optimize storage, and simplify database maintenance.

The following recommendations provide a practical starting point when designing database schemas.

### General Recommendations

1. **Choose the smallest suitable numeric type.** Avoid allocating more storage than your application requires, while allowing room for future growth.
2. **Prefer VARCHAR for variable-length text.** It is generally suitable for names, email addresses, usernames, and addresses.
3. **Use DECIMAL for financial values.** Exact decimal precision is important when working with prices, salaries, balances, and monetary transactions.
4. **Avoid FLOAT and DOUBLE for financial calculations.** These types store approximate values and may introduce rounding differences.
5. **Use BIGINT for very large identifiers.** Consider the expected growth of your application before selecting an identifier type.
6. **Use UNSIGNED when negative values are not required.** This provides a larger positive range for supported integer types.
7. **Choose DATETIME or TIMESTAMP according to your requirements.** Consider date range, timezone behavior, and automatic timestamp management.
8. **Use JSON for flexible structured information.** It is particularly useful when attributes may vary between records.
9. **Use TEXT for longer descriptions and content.** Select the appropriate TEXT variant based on the expected data size.
10. **Use ENUM and SET selectively.** They are useful for predefined values, but frequently changing categories may be better represented using separate lookup tables.
11. **Consider character sets and collations.** Use an appropriate character set, such as `utf8mb4`, for modern multilingual text storage.
12. **Design for future requirements.** Consider expected data growth, application behavior, indexing needs, and maintenance before finalizing your schema.

---

## Official MySQL Documentation

For additional technical details, configuration options, and version-specific behavior, consult the official MySQL documentation:

- [MySQL 8.4 – Data Types](<https://dev.mysql.com/doc/refman/8.4/en/data-types.html>)
- [MySQL 8.4 – Numeric Data Types](<https://dev.mysql.com/doc/refman/8.4/en/numeric-types.html>)
- [MySQL 8.4 – Date and Time Data Types](<https://dev.mysql.com/doc/refman/8.4/en/date-and-time-types.html>)

---

_This reference covers the principal built-in MySQL data types and commonly used aliases. Storage requirements, supported ranges, and specific behaviors may vary depending on the MySQL version, character set, SQL mode, and server configuration._
