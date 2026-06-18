# 第二章　完整語法教學（核心語法）

---
### Table of Contents
> 1. [2.1 標題 Heading](#21-標題-heading)
> 2. [2.2 段落 Paragraph](#22-段落-paragraph)
> 3. [2.2 段落 Paragraph](#23-換行-line-break)
> 4. [2.4 強調 Emphasis](#24-強調-emphasis)
> 5. [2.5 清單 List](#25-清單-list)

---
### 2.1 標題 Heading
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
### 2.2 段落 Paragraph
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
### 2.3 換行 Line Break
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
    兩空格  部分    
    <br>	幾乎全部
```
[↑](#table-of-contents)

---
### 2.4 強調 Emphasis
#### 功能說明
    1. 語意標記。
    2. 不是美化。
#### 粗體
```Markdown
    語法：**重要**
    HTML：<strong>
```
結果：**重要**
#### 斜體
```HTML
    語法：*斜體*
    HTML：<em>
```
結果：*斜體*
#### 粗斜體
    語法：***粗斜***
結果：***粗斜**
#### 刪除線
```HTML
    語法：~~刪除~~
    HTML：<del>
```
結果：~~刪除~~
#### 常見錯誤
    符號不配對：**錯*
#### AST
    Paragraph
    └─ Strong
[↑](#table-of-contents)

---
### 2.5 清單 List
#### 功能說明
    表示集合，不是縮排。
#### 無序清單
    - A
    - B
顯示：
> - A
> - B

HTML：
```HTML
<ul>
<li>A</li>
</ul>
```
#### 有序清單
1. A
2. B

結果：
> 1. A
> 2. B

HTML：
```HTML
    <ol>
```
#### 巢狀清單
    - 主項
      - 子項

結果：
- 主項
  - 子項

#### 使用情境
課程：
    章
    ├─節
    └─活動

#### 常見錯誤
    Tab 與空格混用。

#### AST
    List
    ├─ Item
    └─ Item
[↑](#table-of-contents)

---