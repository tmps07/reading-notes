# 第一章　Markdown 基礎與設計理念

### 1.1 Markdown 是什麼？

Markdown 是一種：

    使用純文字描述文件結構，再轉換成其他格式（通常 HTML）的輕量標記語言（Lightweight Markup Language）。

副檔名通常：

```markdown
.md
.markdown
.mkd
```

核心哲學：

```md
Source 可讀
↓
容易編寫
↓
容易轉換
↓
容易維護
```

與 HTML 不同：

```html
<h1>標題</h1>
<p>內容</p>
```

Markdown：

```md
# 標題
內容
``` 

### 設計目標

原始設計只有兩個：

**目標一：高可讀性（Readable）**

未渲染也容易閱讀。

例如：

```markdown
- 香蕉
- 蘋果
```

比：

```html
<ul>
<li>香蕉</li>
<li>蘋果</li>
</ul>
```

容易閱讀。

**目標二：可寫（Writable）**

減少格式噪音。

例如，不用：

```html
<strong>
```

而使用：

```markdown
**
```

### 1.2 歷史：Markdown 從哪來？

建立時間：2004

作者：

- [John Gruber](https://zh.wikipedia.org/zh-tw/%E7%B4%84%E7%BF%B0%C2%B7%E6%A0%BC%E9%AD%AF%E4%BC%AF)
- [Aaron Swartz](https://zh.wikipedia.org/zh-tw/%E4%BA%9A%E4%BC%A6%C2%B7%E6%96%AF%E6%B2%83%E8%8C%A8)

目標：

讓一般人也能寫 HTML。

最早流程：

```md
Markdown
↓
Perl 腳本
↓
HTML
```

早期：

```md
Markdown.pl
```

負責解析。

當時主流：

```md
HTML 太冗長
Word 不利版本控制
Wiki 語法混亂
```

Markdown 解決：

```md
純文字
+
結構化
+
版本控制
```

後來演化成：

```md
Markdown
├── CommonMark
├── GFM
├── Markdown Extra
├── Pandoc Markdown
└── Obsidian Flavor
```

### 1.3 Markdown 與 HTML 的關係

Markdown 不是替代 HTML。而是：`HTML 的簡化語法`。

流程：

```md
Markdown
↓
Lexer
↓
Parser
↓
AST
↓
Renderer
↓
HTML
↓
Browser
```

例如：

```md

# Hello

這是 **測試**
```

產生：

```html
<h1>Hello</h1>

<p>
這是
<strong>測試</strong>
</p>
```

因此，很多 Markdown 不完整支援 HTML 功能。因為，HTML 有：

```
div
span
script
canvas
svg
iframe
```

Markdown 沒有。這時通常混寫：

``` 
<div>

內容

</div>
``` 

Markdown ≠ HTML 超集合

常見誤解：

❌ Markdown 比 HTML 強

實際：

```
Markdown ⊂ HTML
```

### 1.4 Markdown 如何被解析（Parser）

你熟悉 Compiler 可理解為：

```
Source
↓
Tokenizer
↓
Parser
↓
AST
↓
Renderer
```

Markdown：

```
# A

B
```

Tokenizer：

```
H1
TEXT
PARAGRAPH
```

AST：

```
Document
 ├─ Heading
 └─ Paragraph
```

輸出：

```html
<h1>A</h1>

<p>B</p>
```
#### 真實 Parser 架構

第一層：Lexer，輸入：

```md
## Title
```

輸出：

```
HEADER
TEXT
```

第二層：Parser，建立：

```
AST
```

第三層：Renderer，輸出：

```
HTML
PDF
DOCX
LaTeX
```

#### 常見 Parser

|Parser|語言|
|:--|:--|
|markdown-it|JS|
|marked|JS|
|CommonMark|C|
|Mistune|Python|
|remark|JS|
|Pandoc|Haskell|

### 1.5 Markdown 的限制與優勢

#### 優勢

> ① 可版本控制，適合：`Git`
> ② 純文字，可：`diff`、`merge`、`grep`
> ③ 易轉換，支援：`HTML`、`PDF`、`DOCX`、`EPUB`、`PPT`

#### 短板

> ① 限制：`無完整排版能力`，不能：`grid`、`float`、`flex`。
> ② 無互動能力，如：`onclick`、`script`。
> ③ Syntax 不統一，這是最大問題。
> ④ 不同平台上：`公式`、`Mermaid`、`腳註`結果不同。

### 1.6 Markdown 方言（Flavor）

這是工程上最重要。

同一份：

```md
$$
x^2
$$
```

不同地方不同結果。

#### CommonMark

目標：`統一規格`。

特性：

    ✅ 標題 
    ✅ 清單
    ✅ 引用

沒有：

    ❌ 公式
    ❌ Mermaid

適合：`通用文件`。

### GitHub Flavored Markdown（GFM）

基於 `CommonMark`。增加：

- 表格
- 腳註
- task
- emoji

支援：[GitHub](https://github.com/?utm_source=chatgpt.com)

#### Markdown Extra

增加：

- 表格
- 腳註
- 定義清單

#### Pandoc Markdown

最強。支援：

- LaTeX
- 引用
- 交叉引用
- PDF

適合`教材`使用。

#### Obsidian Flavor

增加：

```
[[雙向連結]]

![[嵌入]]
```

常用於`知識管理`。

### 1.7 Markdown 生態系

Markdown 其實分四層：

```md
Editor
↓
Parser
↓
Renderer
↓
Exporter
```

#### Editor (編輯器)

例如：

- Visual Studio Code
- Obsidian
- Typora

#### Parser (解析)

例如：

- markdown-it
- remark

#### Renderer (渲染)

例如：

- HTML
- PDF

### Exporter (匯出)

例如：

- Pandoc

### 第一章 總結

如果只記三句：

    ① Markdown 是文件語言，不是排版語言
    ② Markdown 幾乎都會先轉成 AST → HTML
    ③ Markdown 沒有唯一標準，要先確認 Flavor

#### 本章作業（教師版）

請實作：

建立：

> markdown-lab/

建立：

> 01-history.md
> 02-parser.md
> 03-flavors.md

內容要求：

> 寫一個 H1
> 一段清單
> 一段 HTML
> 嘗試轉成 HTML

並觀察差異。