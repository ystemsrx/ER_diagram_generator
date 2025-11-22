[English](README.en.md) | [**简体中文**](README.md)

优雅的SQL建表语句转ER图的在线网页工具（SQL to ER Diagram Generator.）

## 快速使用

免费使用，直接访问：[ER Diagram Generator](https://ystemsrx.github.io/ER_diagram_generator/sql2er.html)

受不了了，他妈的B站上搜的DBML/SQL转Chen模型的ER图生成器都他妈的要登录和要钱，没见过这么恶心的东西，直接开源了。

如果需要绘制逻辑模型，请使用 [dbdiagram.io](https://dbdiagram.io/)，免费的。

# SQL/DBML转ER图生成器

一个基于网页的工具，用于从SQL CREATE TABLE语句和DBML格式生成Chen模型ER图。

## 使用方法

1. 在浏览器中打开 `sql2er.html`
2. 在输入区域粘贴您的SQL CREATE TABLE语句或DBML代码
3. 点击"生成ER图"按钮
4. 若对节点位置不满意，可拖拽节点以调整布局；双击节点以修改内容
5. 如果图很复杂，你仅需将每一个矩形（实体）拖拽到期望的位置然后点击“智能优化”按钮，即可自动整理布局

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

![示例1](./assets/eg1.png)

当代码比较复杂时，可能无法直接生成出满意的图，此时可以先点击右上角的**强制对齐**按钮，然后再点击**智能布局**，即可自动整理一个新的布局，理论上此时应当比较整齐，仅需微调即可。

若在少数情况下仍然比较乱，可以**手动**先将矩形（实体）拖拽到合适位置（无需拖动其他的），然后点击**智能优化**按钮，这将会自动整理布局。

例如：

<table>
<tr>
<td width="50%">
<h4>直接生成</h4>
<img src="./assets/eg2.png" alt="Direct Generation"/>
</td>
<td width="50%">
<h4>先对齐后智能布局</h4>
<img src="./assets/eg2_opt.png" alt="Optimized Layout"/>
</td>
</tr>
</table>

## 开源协议

MIT License 