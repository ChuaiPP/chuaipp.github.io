---
title: Mermaid 图表使用指南
description: 在 Markdown 中使用 Mermaid 绘制流程图、序列图、甘特图等图表
date: 2025-06-22
tags: [教程, Mermaid, 图表]
category: 教程
cover: https://mermaid.js.org/images/header.png
---

Mermaid 是一个基于 JavaScript 的图表绘制工具，可以通过类似 Markdown 的语法生成各种图表。本篇文章将展示各种 Mermaid 图表的用法。

## 流程图

```mermaid
graph TD
    A[开始] --> B{是否需要登录?}
    B -->|是| C[输入账号密码]
    B -->|否| D[直接访问]
    C --> E{验证成功?}
    E -->|是| D
    E -->|否| C
    D --> F[结束]
```

## 序列图

```mermaid
sequenceDiagram
    participant U as 用户
    participant B as 浏览器
    participant S as 服务器
    participant D as 数据库

    U->>B: 输入查询条件
    B->>S: 发送搜索请求
    S->>D: 查询数据库
    D-->>S: 返回结果
    S-->>B: 返回 JSON 数据
    B-->>U: 展示搜索结果
```

## 类图

```mermaid
classDiagram
    class User {
        +String name
        +String email
        +login()
        +logout()
    }

    class Article {
        +String title
        +String content
        +Date createdAt
        +publish()
    }

    class Comment {
        +String text
        +Date createdAt
        +create()
    }

    User "1" --> "*" Article : writes
    User "1" --> "*" Comment : creates
    Article "1" --> "*" Comment : has
```

## 甘特图

```mermaid
gantt
    title 项目开发计划
    dateFormat  YYYY-MM-DD
    section 第一阶段
    需求分析           :a1, 2025-06-01, 7d
    UI 设计            :a2, after a1, 5d
    section 第二阶段
    前端开发           :b1, after a2, 10d
    后端开发           :b2, after a2, 12d
    section 第三阶段
    测试               :c1, after b2, 5d
    部署上线           :c2, after c1, 2d
```

## 饼图

```mermaid
pie title 技术栈占比
    "JavaScript" : 40
    "TypeScript" : 25
    "CSS" : 15
    "HTML" : 10
    "其他" : 10
```

## 状态图

```mermaid
stateDiagram-v2
    [*] --> 待审核
    待审核 --> 审核通过 : 通过
    待审核 --> 审核拒绝 : 拒绝
    审核通过 --> 已发布 : 发布
    审核拒绝 --> 待审核 : 重新提交
    已发布 --> [*]
```

## ER 图

```mermaid
erDiagram
    USER ||--o{ POST : creates
    POST ||--o{ COMMENT : has
    USER ||--o{ COMMENT : writes
    POST }o--|| CATEGORY : belongs_to

    USER {
        int id PK
        string name
        string email
    }

    POST {
        int id PK
        string title
        text content
        date created_at
    }

    COMMENT {
        int id PK
        text content
        date created_at
    }

    CATEGORY {
        int id PK
        string name
    }
```

## 总结

Mermaid 支持多种图表类型：

- **流程图** - 适合展示业务流程和决策逻辑
- **序列图** - 适合展示组件间的交互
- **类图** - 适合展示面向对象的设计
- **甘特图** - 适合项目管理和时间规划
- **饼图** - 适合数据可视化
- **状态图** - 适合展示状态转换
- **ER 图** - 适合数据库设计

在 Markdown 中使用 ` ```mermaid ` 代码块即可，博客会自动渲染为图表。
