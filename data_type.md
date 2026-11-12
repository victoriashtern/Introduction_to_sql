
# MySQL Data Types – Complete Reference

MySQL data types define what kind of information a table column can store, such as numbers, text, dates, times, binary data, and geographical information.

## Table of Contents

1. [Numeric Data Types](#1-numeric-data-types)
2. [String and Text Data Types](#2-string-and-text-data-types)
3. [Date and Time Data Types](#3-date-and-time-data-types)
4. [JSON Data Type](#4-json-data-type)
5. [Spatial (GIS) Data Types](#5-spatial-gis-data-types)
6. [Common MySQL Type Aliases](#6-common-mysql-type-aliases)
7. [Practical Examples](#7-practical-examples-choosing-the-right-data-type)
8. [Complete CREATE TABLE Example](#8-complete-create-table-example)
9. [Quick Guide](#9-quick-guide-which-type-should-you-use)
10. [Recommendations](#10-recommendations)

---

## 1. Numeric Data Types

Numeric data types store integers, decimal numbers, and floating-point values.

| Data Type | Storage | Signed Range | Unsigned Range | Description | Example | Typical Use |
|---|---:|---|---|---|---|---|
| TINYINT | 1 byte | -128 to 127 | 0 to 255 | Small integer | 25 | Age, status, flags |
| SMALLINT | 2 bytes | -32,768 to 32,767 | 0 to 65,535 | Small integer | 1500 | Small quantities |
| MEDIUMINT | 3 bytes | -8,388,608 to 8,388,607 | 0 to 16,777,215 | Medium integer | 50000 | Medium counts |
| INT / INTEGER | 4 bytes | -2,147,483,648 to 2,147,483,647 | 0 to 4,294,967,295 | Standard integer | 100000 | IDs, quantities |
| BIGINT | 8 bytes | -9.22 × 10¹⁸ to 9.22 × 10¹⁸ | 0 to 1.84 × 10¹⁹ | Large integer | 9000000000 | Large IDs, counters |
| DECIMAL(p,s) | Variable | Depends on precision | Depends on precision | Exact decimal number | DECIMAL(10,2) → 1250.75 | Money, prices |
| NUMERIC(p,s) | Variable | Depends on precision | Depends on precision | Synonym for DECIMAL | NUMERIC(8,2) | Financial values |
| FLOAT | 4 bytes | Approx. ±3.4 × 10³⁸ | N/A | Approximate floating-point number | 12.56 | Scientific calculations |
| DOUBLE | 8 bytes | Approx. ±1.8 × 10³⁰⁸ | N/A | Double-precision floating-point number | 12345.6789 | Measurements |
| BIT(n) | Up to 64 bits | N/A | 0 to 2ⁿ - 1 | Bit-value field | BIT(1) | Binary flags |
| BOOLEAN | 1 byte | Commonly 0 or 1 | N/A | Alias for TINYINT | TRUE / FALSE | True/false values |
| BOOL | 1 byte | Commonly 0 or 1 | N/A | Alias for TINYINT | TRUE / FALSE | True/false values |

### Numeric Data Type Notes

- UNSIGNED removes negative values for supported integer types.
- DECIMAL(p,s):
  - p = total number of digits.
  - s = number of digits after the decimal point.
  - Example: DECIMAL(10,2) allows 10 total digits, including 2 decimal places.
- FLOAT and DOUBLE use approximate values. Avoid them for financial calculations.
- BIT(n) supports 1–64 bits.
- Boolean values are stored as 0 (false) and 1 (true), although MySQL permits other integer values.
- BIGINT ranges above are rounded for readability.

Example:

```
CREATE TABLE products (
    id INT UNSIGNED,
    quantity SMALLINT UNSIGNED,
    price DECIMAL(10,2),
    discount FLOAT
);
```

---

## 2. String and Text Data Types

String data types store text, characters, and binary information.

| Data Type | Maximum Size | Description | Example | Typical Use |
|---|---:|---|---|---|
| CHAR(n) | 255 characters | Fixed-length string | 'John' | Country codes, fixed codes |
| VARCHAR(n) | 65,535 bytes (row-dependent) | Variable-length string | 'John Smith' | Names, emails |
| BINARY(n) | 255 bytes | Fixed-length binary data | X'4A4F' | Binary identifiers |
| VARBINARY(n) | 65,535 bytes (row-dependent) | Variable-length binary data | X'4A4F484E' | Binary values |
| TINYTEXT | 255 bytes | Very short text | 'Hello World' | Short text |
| TEXT | 65,535 bytes | Standard text | 'Article content...' | Descriptions, comments |
| MEDIUMTEXT | 16,777,215 bytes | Medium-sized text | 'Long article...' | Large documents |
| LONGTEXT | 4,294,967,295 bytes | Very large text | 'Very long content...' | Large text storage |
| TINYBLOB | 255 bytes | Small binary data | X'414243' | Small binary files |
| BLOB | 65,535 bytes | Binary data | X'FFD8FF' | Images, files |
| MEDIUMBLOB | 16,777,215 bytes | Medium binary data | Binary file | Medium files |
| LONGBLOB | 4,294,967,295 bytes | Large binary data | Binary file | Large files |
| ENUM | Up to 65,535 members | One value from a predefined list | 'ACTIVE' | Status, categories |
| SET | Up to 64 members | Zero or more predefined values | 'READ,WRITE' | Multiple permissions |

### String Data Type Notes

- CHAR is useful for fixed-length values.
- VARCHAR is generally preferred for names, addresses, and emails.
- TEXT is useful for longer descriptions and comments.
- BLOB stores binary data rather than text.
- ENUM allows only one predefined value.
- SET allows multiple predefined values.
- Text maximum sizes are measured in bytes, not necessarily characters.

Example:

```
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

## 3. Date and Time Data Types

Date and time data types store dates, times, and timestamps.

| Data Type | Storage | Range | Description | Example | Typical Use |
|---|---:|---|---|---|---|
| DATE | 3 bytes | 1000-01-01 to 9999-12-31 | Stores date only | '2026-11-12' | Birthdays, registration dates |
| TIME | 3 bytes (+ fractional seconds) | -838:59:59 to 838:59:59 | Stores time or duration | '14:30:00' | Opening times, durations |
| DATETIME | 5 bytes (+ fractional seconds) | 1000-01-01 to 9999-12-31 | Stores date and time | '2026-11-12 14:30:00' | Orders, appointments |
| TIMESTAMP | 4 bytes (+ fractional seconds) | 1970-01-01 to 2038-01-19 (UTC range, approximately) | Stores date and time with timezone conversion | '2026-11-12 14:30:00' | Created/updated timestamps |
| YEAR | 1 byte | 1901 to 2155, or 0000 | Stores a year | 2026 | Manufacturing year |

### Fractional Seconds

MySQL supports fractional seconds precision from 0 to 6.

- TIME(3) – milliseconds.
- DATETIME(6) – microseconds.
- TIMESTAMP(6) – microseconds.

### Date and Time Notes

- DATE stores only a date.
- TIME can represent negative or positive durations.
- DATETIME does not perform automatic timezone conversion.
- TIMESTAMP converts between the session timezone and UTC.
- TIMESTAMP has a narrower supported range than DATETIME.

Example:

```
CREATE TABLE appointments (
    id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    appointment_date DATE,
    appointment_time TIME,
    appointment_datetime DATETIME,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 4. JSON Data Type

The JSON data type stores validated JSON documents.

| Data Type | Description | Example | Typical Use |
|---|---|---|---|
| JSON | Stores validated JSON documents | {"name":"John","age":25} | API responses, flexible attributes |

### JSON Example

```
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

### JSON Notes

- MySQL validates JSON when inserting or updating values.
- JSON supports objects, arrays, strings, numbers, booleans, and null.
- JSON fields can be queried using JSON functions and operators.
- JSON columns cannot be indexed directly in the same way as ordinary columns. Generated columns and multi-valued indexes can be used for indexing appropriate JSON values.

---

## 5. Spatial (GIS) Data Types

Spatial data types store geographical and geometric information.

| Data Type | Description | Example | Typical Use |
|---|---|---|---|
| GEOMETRY | Any geometry type | Geometry object | General spatial data |
| POINT | A single location | POINT(10 20) | GPS coordinates |
| LINESTRING | A sequence of connected points | LINESTRING(0 0,10 10) | Roads, routes |
| POLYGON | An enclosed area | POLYGON((0 0,10 0,10 10,0 10,0 0)) | Property boundaries |
| MULTIPOINT | Multiple points | Multiple coordinates | Multiple locations |
| MULTILINESTRING | Multiple lines | Multiple line segments | Road networks |
| MULTIPOLYGON | Multiple polygons | Multiple areas | Geographic regions |
| GEOMETRYCOLLECTION | Collection of different geometries | Point + LineString | Complex geographic data |

### Spatial Example

```
CREATE TABLE locations (
    id INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    coordinates POINT NOT NULL,
    SPATIAL INDEX (coordinates)
);
```

---

## 6. Common MySQL Type Aliases

Some MySQL data types are alternative names for existing types.

| Alias | Equivalent Type | Example |
|---|---|---|
| INTEGER | INT | INTEGER |
| BOOL | TINYINT | BOOL |
| BOOLEAN | TINYINT | BOOLEAN |
| NUMERIC | DECIMAL | NUMERIC(10,2) |
| DEC | DECIMAL | DEC(10,2) |
| FIXED | DECIMAL | FIXED(10,2) |
| REAL | Usually DOUBLE | REAL |
| DOUBLE PRECISION | DOUBLE | DOUBLE PRECISION |

Note: REAL behavior can depend on the REAL_AS_FLOAT SQL mode.

---

## 7. Practical Examples: Choosing the Right Data Type

Here are common choices when designing a real-world database.

| Database Field | Recommended Type | Example Value | Reason |
|---|---|---|---|
| User ID | BIGINT UNSIGNED | 100001 | Large identifier |
| First name | VARCHAR(100) | John | Variable-length text |
| Last name | VARCHAR(100) | Smith | Variable-length text |
| Email | VARCHAR(255) | john@email.com | Email address |
| Password hash | VARCHAR(255) | a8f5f167... | Store hashed passwords |
| Age | TINYINT UNSIGNED | 25 | Small positive number |
| Price | DECIMAL(10,2) | 199.99 | Exact monetary value |
| Quantity | INT UNSIGNED | 500 | Whole-number quantity |
| Discount | DECIMAL(5,2) | 15.50 | Percentage |
| Is active | BOOLEAN | TRUE | Yes/no value |
| Description | TEXT | Product description... | Longer text |
| Profile image | BLOB | Binary image data | Image storage |
| Birth date | DATE | 1995-05-20 | Date only |
| Created date | TIMESTAMP | 2026-11-12 15:30:00 | Record creation time |
| Appointment | DATETIME | 2026-11-15 10:30:00 | Date and time |
| User preferences | JSON | {"theme":"dark"} | Flexible data |

---

## 8. Complete CREATE TABLE Example

This example combines several MySQL data types.

```
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
---

## 9. Quick Guide: Which Type Should You Use?

| If You Want to Store... | Use |
|---|---|
| Small whole numbers | TINYINT |
| Normal whole numbers | INT |
| Very large whole numbers | BIGINT |
| Money | DECIMAL |
| Approximate decimal calculations | FLOAT or DOUBLE |
| Short text | VARCHAR |
| Fixed-length text | CHAR |
| Long text | TEXT |
| Large text documents | LONGTEXT |
| Binary files | BLOB |
| Dates | DATE |
| Time | TIME |
| Date and time | DATETIME |
| Automatically managed timestamps | TIMESTAMP |
| True/false | BOOLEAN |
| JSON documents | JSON |
| Geographical coordinates | POINT |
| Predefined single choices | ENUM |
| Multiple predefined choices | SET |

---

## 10. Recommendations

- Prefer VARCHAR for names, emails, and addresses.
- Prefer DECIMAL for prices and financial calculations.
- Prefer BIGINT UNSIGNED for IDs when you expect very large numbers.
- Prefer DATETIME when you need a wide date range or do not want automatic timezone conversion.
- Prefer TIMESTAMP for automatically managed creation and update timestamps.
- Prefer JSON when storing flexible structured data.
- Prefer TEXT for descriptions and longer content.
- Avoid FLOAT and DOUBLE for financial calculations.
- Use UNSIGNED when negative values are not needed.
- Choose data types based on the expected size and purpose of the data.

---

## Official Documentation

[MySQL 8.4 – Complete Data Types Reference](https://dev.mysql.com/doc/refman/8.4/en/data-types.html)

[MySQL 8.4 – Numeric Data Types](https://dev.mysql.com/doc/refman/8.4/en/numeric-types.html)

[MySQL 8.4 – Date and Time Data Types](https://dev.mysql.com/doc/refman/8.4/en/date-and-time-types.html)

---

*This reference covers the main built-in MySQL data types and aliases. Storage sizes and behavior may depend on MySQL version, character set, SQL mode, and configuration.*

