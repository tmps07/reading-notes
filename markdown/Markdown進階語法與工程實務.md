# 第二章（下）進階語法與工程實務
---
### Table of Contents
> [2.12 錨點 Anchor](#212-錨點)
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