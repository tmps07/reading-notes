# 第二章　完整語法教學（核心語法）

---
### Table of Contents
> 1. [2.1 標題（Heading）](#21-標題heading)
> 2. [2.2 段落（Paragraph）](#22-段落paragraph)

---
### 2.1 標題（Heading）
#### 功能說明：
```Markdown
    用來 `表示文件階層`。
    類似：
        HTML → h1~h6
        Word → 標題樣式
        LaTeX → section
    不要把標題當字體大小，它是「文件結構」。
```
#### 基本語法：
```Markdown
    #       H1
    ##      H2
    ###     H3
    ####    H4
    #####   H5
    ######  H6
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
#### 常見錯誤
```Markdown
    ❌ 跳層：
        # A
        #### B
    正確：
        # A
        ## B
```
#### 平台支援
平台	支援
```Markdown
    [✓] GitHub
    [✓] Obsidian
    [✓] VS Code
    [✓] Typora
    [✓] Notion
```
#### Parser／AST
    Document
    └── Heading(level=2)
[↑](#table-of-contents)

---
### 2.2 段落（Paragraph）
#### 功能說明
    表示文字區塊。Markdown：沒有 `<p>`，由 Parser 自動推導。
#### 基本語法
```Markdown
第一段  

第二段

顯示結果

第一段

第二段
```
#### 對應 HTML
```HTML
    <p>第一段</p>

    <p>第二段</p>
```
#### 使用情境
```Markdown
    教學：
        標題
        ↓
        說明段落
        ↓
        範例
```
#### 常見錯誤
```Markdown
    ❌ 少空行：
        第一段
        第二段
```
可能合併。

#### AST
    Document
    └─ Paragraph
[↑](#table-of-contents)

---
### 2.3 換行（Line Break）
#### 功能說明：
    換行 ≠ 新段落。
#### 基本語法
```Markdown
    方法一：
        第一行·· （..代表尾端的兩空格）
        第二行
    方法二：
        第一行<br>
        第二行
    HTML：<br>
```
#### 常見錯誤
```Markdown
    很多人以為：
        A
        B
    會換行。結果不一地。
```
#### 平台支援方式
```Markdown
    兩空格	部分    
    <br>	幾乎全部
```
[↑](#table-of-contents)

---
