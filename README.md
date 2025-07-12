[English](README.en.md) | [**简体中文**](README.md)

## 快速使用

访问：[ER Diagram Generator](https://ystemsrx.github.io/ER_diagram_generator/sql2er.html)

# SQL/DBML转ER图生成器

一个基于网页的工具，用于从SQL CREATE TABLE语句和DBML格式生成Chen模型ER图。

## 使用方法

1. 在浏览器中打开 `sql2er.html`
2. 在输入区域粘贴您的SQL CREATE TABLE语句或DBML代码
3. 点击"生成ER图"按钮
4. 查看并与生成的ER图进行交互

## 支持格式

### SQL示例
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

### DBML示例
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

## Chen模型元素

- **矩形**: 实体（表）
- **菱形**: 关系（外键）
- **椭圆**: 属性（列）
- **下划线**: 主键属性

## 示例

![示例1](https://github.com/ystemsrx/ER_diagram_generator/blob/master/assets/eg1.png?raw=true)

## 开源协议

MIT License 