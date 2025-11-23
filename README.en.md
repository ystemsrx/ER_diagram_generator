[**English**](README.en.md) | [简体中文](README.md)

## Quick Start

Visit: [ER Diagram Generator](https://ystemsrx.github.io/ER_diagram_generator/sql2er.html)

If you need to draw a logical model, please use [dbdiagram.io](https://dbdiagram.io), which is free.

# SQL/DBML to ER Diagram Generator

A web-based tool for generating Chen model ER diagrams from SQL CREATE TABLE statements and DBML format.

## Usage

1. Open `sql2er.html` in your web browser
2. Paste your SQL CREATE TABLE statements or DBML code in the input area
3. Click "Generate ER Diagram" button
4. If you're not satisfied with the node positions, you can drag nodes to adjust the layout; double-click a node to edit its content
5. If the diagram is complex, simply drag each rectangle (entity) to the desired position and click the "Smart Optimization" button to automatically organize the layout

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

## Differences from Standard Chen Model

**Relationship Naming:** In the standard Chen model, diamonds (relationships) should use semantic names (such as "belongs to", "owns"). This tool simplifies usage by displaying foreign key field names by default.

**Entity and Attribute Naming:** The standard Chen model recommends using business terminology. This tool displays database table names and column names directly by default.

**Custom Modifications:**
- Double-click graphical elements to edit display content directly
- Or modify in source code (DBML/SQL) and regenerate

> 💡 **Reference Standard Examples:** [ER Diagram Generator](https://ystemsrx.github.io/ER_diagram_generator/sql2er.html)

## Chen Model Elements

- **Rectangle**: Entity (Table)
- **Diamond**: Relationship (Foreign Key)
- **Ellipse**: Attribute (Column)
- **Underlined**: Primary Key attribute

## Example

![Example 1](./assets/eg1.png)

When the code is complex, direct generation may not produce a satisfactory diagram. In this case, you can first click the **Force Alignment** button in the top right corner, and then click **Smart Layout** to automatically organize a new layout, which should be relatively neat in theory and only require minor adjustments.

The **Force2** toggle is disabled by default. If the generated diagram looks messy, you can enable this toggle and generate again. It provides a more stable structure.

If in rare cases it's still messy, you can **manually** drag the rectangles (entities) to suitable positions (no need to move other elements), and then click the **Smart Layout** button, which will automatically organize the layout.

For example:

<table>
<tr>
<td width="50%">
<h4>Direct Generation</h4>
<img src="./assets/eg2.png" alt="Direct Generation"/>
</td>
<td width="50%">
<h4>After Smart Optimization</h4>
<img src="./assets/eg2_opt.png" alt="Optimized Layout"/>
</td>
</tr>
</table>

## License

MIT License 