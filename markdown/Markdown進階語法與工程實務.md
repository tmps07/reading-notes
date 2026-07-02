# 第二章（下）進階語法與工程實務
---
### Table of Contents
> [2.12 錨點 Anchor](#212-錨點)  
> [2.13 腳註 Footnote](#213-腳註-footnote)  
> [2.14 任務清單 Task List](#214-任務清單-task-list)  
> [2.15 HTML 混用 Raw HTML](#215-html-混用-raw-html)
---
### 2.12 錨點
#### 功能說明
```HTML
    讓文件可以：
        內部跳轉
        建目錄（TOC）
        章節引用
    類似：
        <a href="#chapter">
```
#### 基本語法
    Markdown：
        [跳到第三章](#第三章)
[跳到第三章](#第三章)
#### 連結目標：
## 第三章
##### 對應 HTML
```HTML
<a href="#第三章">
```
#### 使用情境
    教材：
        目錄
        ↓
        單元一
        ↓
        單元二
#### 進階技巧
    GitHub：
        # Hello World
    自動：
        #hello-world
    跳轉：
        [Go](#hello-world)
#### 常見錯誤
    中文與空白。
    例如：
        # 我的 第一章
        平台產生不同 ID。
    建議：
        # chapter-01
#### 平台支援
|平台|支援|
|:--|:--|
|GitHub|✓|
|Obsidian|✓|
|VS Code|✓|
|Notion|有限|

#### AST
    Link
    ↓
    Heading
[↑](#table-of-contents)

---
### 2.13 腳註 Footnote
#### 功能說明
    建立註解。常見於：
        教材
        學術文件
        論文
#### 基本語法
    文字[^1]

    [^1]: 補充說明
#### 顯示結果
    文字¹
#### HTML
```HTML
    <sup>
```
#### 使用情境
    數學教材：
    平方根¹

#### 進階技巧
    多段：
    [^1]:
    第一段

    第二段
#### 常見錯誤
    缺少定義：
    [^1]

    無內容。

#### 支援
|平台|支援|
|:--|:--|  
|GitHub|✓| 
|Obsidian|✓|  
|Notion|✗|

[↑](#table-of-contents)

---
### 2.14 任務清單 Task List
#### 功能說明
    核取方塊。
#### 基本語法
    - [ ] 未完成
    - [x] 已完成
#### 結果：
> - [ ] 未完成
> - [ ] 已完成
#### HTML
```HTML
<input>
```
#### 使用情境
    教師：
        □ 出題
        □ 上課
        □ 評量
#### 進階技巧
    巢狀：
    - [x] 第一章
      - [ ] 第二章
#### 常見錯誤
    缺空格：
        -[ ]
#### 支援
|平台|支援|
|:--|:--|
|GitHub|✓|
|Obsidian|✓|
|Typora|✓|

[↑](#table-of-contents)

---
### 2.15 HTML 混用 Raw HTML
#### 功能說明
    突破 Markdown 限制。
#### 基本語法
```HTML
<div>
    內容
</div>
```
#### 顯示結果
    HTML 直接渲染。
#### 使用情境
> 控制：
> - 寬度
> - 顏色
> - 排版
#### 進階技巧
> ```HTML
> 圖片：
> <img width="300">
> 影片：
> <iframe>
> 折疊：
> <details>
> ```
#### 常見錯誤
    HTML 被過濾。
    例如：
        GitHub：
        script 禁止
#### 支援
|平台|HTML|
|:--|:--|
|GitHub|部分|
|Obsidian|✓|
|Notion|限制|

[↑](#table-of-contents)

---