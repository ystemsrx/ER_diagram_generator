[**English**](README.en.md) | [简体中文](README.md)

## Quick Start

Visit: [ER Diagram Generator](https://ystemsrx.github.io/ER_diagram_generator/sql2er.html)

# SQL/DBML to ER Diagram Generator

A web-based tool for generating Chen model ER diagrams from SQL CREATE TABLE statements and DBML format.

## Usage

1. Open `sql2er.html` in your web browser
2. Paste your SQL CREATE TABLE statements or DBML code in the input area
3. Click "Generate Chen Model ER Diagram" button
4. View and interact with the generated ER diagram

## Supported Formats

### SQL Example
```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE
);

CREATE TABLE posts (
    id INT PRIMARY KEY,
    author_id INT,
    title VARCHAR(255),
    FOREIGN KEY (author_id) REFERENCES users(id)
);
```

### DBML Example
```dbml
Table users {
  id INT [pk]
  username VARCHAR(255) [not null]
  email VARCHAR(255) [unique]
}

Table posts {
  id INT [pk]
  author_id INT
  title VARCHAR(255)
}

Ref: posts.author_id > users.id
```

## Chen Model Elements

- **Rectangle**: Entity (Table)
- **Diamond**: Relationship (Foreign Key)
- **Ellipse**: Attribute (Column)
- **Underlined**: Primary Key attribute

## Example

![Example 1](https://github.com/ystemsrx/ER_diagram_generator/blob/master/assets/eg1.png?raw=true)

## License

MIT License 