# 1. Markdown 是什麼？

Markdown（`.md`）是一種輕量標記語言（Lightweight Markup Language）。

##### 目標：

- 易寫（純文字） 
- 易讀（不看渲染也能理解）
- 易轉換（HTML、PDF、Word…）

##### 範例：
```Markdown
# 我的筆記

今天學 Markdown。

- 第一點
- 第二點
```
# 2. 標題（Heading）

##### 語法
```Markdown
# H1
## H2
### H3
#### H4
##### H5
###### H6
```
##### 使用情境

    ✅ 文件章節
    ✅ README
    ✅ 筆記

##### 常見錯誤

    ❌ 少空格

# 3. 段落與換行

##### 語法
```Markdown
第一段

第二段
```

##### 換行
```Markdwon
第一行  （這裡行尾有兩個空格）
第二行
```
或：
```Markdown
第一行<br>
第二行
```

##### 常見錯誤

    ❌ 直接 Enter：

# 4. 強調文字

- 粗體：`**粗體**` → **粗體**
- 斜體：`*斜體*`　→ *斜體*
- 粗斜體：`***粗斜體***` → ***粗斜體***
- 刪除線：`~~刪除~~` → ~~刪除~~

##### 常見錯誤

    混用：**錯誤*

# 5. 清單（List）

##### 無序
```Markdown
    - A
    - B
```
  - A
  - B

##### 有序
```Markdown
1. A
2. B
```
1. A
2. B

##### 巢狀
```
- 主項
  - 子項
```
- 主項
    - 子項

##### 常見錯誤

    縮排不一致。

# 6. 連結

##### 語法
```
[Google](https://google.com)
```
> [Google](https://google.com)&nbsp;&nbsp;&nbsp;&nbsp;[東門國小](https://www.tmps.hc.edu.tw)

##### 同頁跳轉
```
[到第三章](#第三章)
```

##### 常見錯誤

    忘記括號：

# 7. 圖片 

##### 語法
```
![我](./mdImage/tmps07.png)
指定尺寸（需使用 HTML 標籤）
<img src="./mdImage/tmps07.png" width="300">
```
![我](./mdImage/tmps07.png)

##### 使用情境
    README
    部落格

# 8. 引用（Blockquote）
```
> 第一層
>> 第二層
```
> 第一層
>> 第二層

# 9. 程式碼

##### 行內
使用 \`print()\` → 使用 `print()`

##### 區塊
> \`\`\`python
print("hello")
\`\`\`
```
print("hello")
```

##### 常見支援語言
- python
- js
- cpp
- java
- html
- css

# 10. 表格

    |姓名|年齡|
    |---|---|
    |小明|10|

|姓名|年齡|
|---|---|
|小明|10|

##### 對齊

    |左|中|右|
    |:--|:-:|--:|

##### 常見錯誤
    欄數不一致。

# 11. 分隔線

    ---

或

    ***

# 12. 核取方塊（Task List）

```
- [x] 完成
- [ ] 未完成
```

- [x] 完成
- [ ] 未完成

##### 支援情況

    ✅ GitHub
    ✅ Obsidian
    ⚠️ 部分編輯器不支援

# 13. HTML 混用

```html
<details>
<summary>展開</summary>

內容

</details>
```

<details> <summary>展開</summary>

內容

</details>

# 14. 數學公式（LaTeX）

你提到的重要問題。

##### 行內

`$E=mc^2$`
→
$E=mc^2$

##### 區塊

```
$$
\int x dx
$$
```
→
$$
\int x dx
$$

##### 常見公式

分數：
```
\frac{a}{b}
```
平方：
```
x^2
```
矩陣：
```
\begin{bmatrix}
1&2\\
3&4
\end{bmatrix}
```

##### 為何有些編輯器不顯示？

因為公式其實不是標準 Markdown。通常靠：

- KaTeX
- MathJax

額外渲染。

# 15. Mermaid 流程圖（進階）

```Markdown
graph TD
A-->B
```
產生流程圖。

##### 支援：
- GitHub
- Obsidian
- VS Code

# 16. 腳註

```
文字[^1]

[^1]: 註解
```

# 17. 目錄（TOC）

```
[TOC]
```

支援有限。

# 18. YAML Front Matter

常見於部落格。

```
---
title: 我的文章
date: 2026
---
```
# 19. Markdown 方言差異（超重要）
| 功能 | CommonMark | GitHub | Obsidian | Notion |
| :-- | :-- | :-- | :-- | :-- |
| 表格 | ✓ | ✓ | ✓ | ✓ |
| 公式 | ✗ | ✓ | ✓ | 部分 |
| Mermaid | ✗ | ✓ | ✓ | ✗ |
| Task | ✗ | ✓ | ✓ | ✓ | 
| HTML | 部分 | ✓ | ✓ | 限制 |
