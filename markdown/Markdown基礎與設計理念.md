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

```markdown
Source 可讀
↓
容易編寫
↓
容易轉換
↓
容易維護
```

與 HTML 不同：

    HTML：

    <h1>標題</h1>

    <p>內容</p>

    Markdown：

    # 標題

    內容

### 設計目標

原始設計只有兩個：

**目標一：可讀（Readable）**

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

例如：

不用：

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