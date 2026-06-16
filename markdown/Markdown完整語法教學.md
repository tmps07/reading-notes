# 第二章　完整語法教學（核心語法）
---
### Table of Contents
> 1. [2.1 標題（Heading）](#21-標題heading)
---
### 2.1 標題（Heading）
#### 功能說明：用來 `表示文件階層`。
```Markdown
類似：
    HTML → h1~h6
    Word → 標題樣式
    LaTeX → section
不要把標題當字體大小，它是「文件結構」。
```
#### 基本語法：
```md
# H1
## H2
### H3
#### H4
##### H5
###### H6
```
#### 顯示結果
```Markdown
    H1
    └─ H2
       └─ H3
```
#### 對應 HTML
```HTML
## 教學
    ↓
<h2>教學</h2>
```
#### 使用情境
```Markdown
① 教材：
    第一章
    ├─ 第一節
    └─ 第二節
② 技術文件：
    API
    ├─ Auth
    ├─ User
    └─ Payment
```
#### 進階技巧
```Markdown
可自動產生 TOC。例如：
### 第三章
可跳（類似連結）：[跳轉](#第三章)
```
[Table of Contents](#table-of-contents)
---

