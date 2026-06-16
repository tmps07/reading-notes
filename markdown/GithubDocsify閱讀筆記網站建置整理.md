# Docsify 個人閱讀筆記網站建置總整理

## 一、目前完成的功能

目前已完成：

1. 使用 Docsify 建立閱讀筆記網站
2. 使用 GitHub Pages 部署
3. 使用 SSH Key 連接 GitHub
4. 使用 GitHub Actions 自動產生 `_sidebar.md`
5. 新增 Markdown 檔案後，側邊欄目錄可自動更新
6. 支援：

   * Markdown 筆記
   * 程式碼高亮
   * LaTeX 數學公式
   * 自動部署
   * 自動目錄

---

# 二、專案資料夾結構

目前建議結構如下：

```txt
gitNote/
├── .github/
│   └── workflows/
│       └── update-sidebar.yml
├── gas/
│   └── README.md
├── markdown/
│   ├── mdImage/
│   ├── README.md
│   └── Markdown quick View.md
├── poetry/
│   ├── mdImage/
│   ├── README.md
│   └── 揚州瘦馬.md
├── programming/
│   └── README.md
├── science/
│   └── README.md
├── stem/
│   └── README.md
├── .gitignore
├── .nojekyll
├── README.md
├── _sidebar.md
├── index.html
└── package.json
```

---

# 三、SSH Key 設定步驟

## 1. 檢查是否已有 SSH Key

```bash
ls ~/.ssh
```

若已有：

```txt
id_ed25519
id_ed25519.pub
```

可略過產生步驟。

---

## 2. 建立 SSH Key

使用 GitHub 帳號 Email：

```bash
ssh-keygen -t ed25519 -C "tmps07@gmail.com"
```

一路按 Enter。

---

## 3. 啟動 ssh-agent

```bash
eval "$(ssh-agent -s)"
```

---

## 4. 加入 SSH Key

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## 5. 複製 Public Key

macOS：

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

---

## 6. 到 GitHub 加入 SSH Key

GitHub：

```txt
右上角頭像
→ Settings
→ SSH and GPG keys
→ New SSH key
```

填入：

```txt
Title: MacBook-GitNote
Type: Authentication Key
Key: 貼上剛剛複製的內容
```

---

## 7. 測試連線

```bash
ssh -T git@github.com
```

成功會看到：

```txt
Hi tmps07! You've successfully authenticated.
```

---

# 四、Git 基本操作流程

## 第一次初始化

```bash
cd ~/Documents/gitNote

git init
git add .
git commit -m "init docsify site"
git branch -M main
git remote add origin git@github.com:tmps07/reading-notes.git
git push -u origin main
```

---

## 日常新增筆記流程

因為 GitHub Actions 會自動更新 `_sidebar.md`，所以建議每次開始前先同步：

```bash
cd ~/Documents/gitNote

git pull --rebase origin main
```

新增或修改筆記後：

```bash
git add .
git commit -m "add new note"
git push
```

---

## 刪除筆記流程

例如刪除：

```txt
poetry/test.md
```

執行：

```bash
rm poetry/test.md

git add .
git commit -m "remove poetry test"

git pull --rebase origin main
git push
```

---

# 五、GitHub Pages 設定

GitHub Repository：

```txt
reading-notes
```

設定位置：

```txt
Settings
→ Pages
```

設定：

```txt
Source: Deploy from branch
Branch: main
Folder: /root
```

網站網址：

```txt
https://tmps07.github.io/reading-notes/
```

---

# 六、GitHub Actions 自動產生目錄

## 功能說明

目前使用 GitHub Actions 自動更新 `_sidebar.md`。

流程如下：

```txt
新增 Markdown 檔案
↓
git push
↓
GitHub Actions 執行 update-sidebar.yml
↓
自動產生 _sidebar.md
↓
自動 commit 回 GitHub
↓
GitHub Pages 重新部署
↓
網站目錄更新
```

---

## 注意事項

以後不要手動長期維護 `_sidebar.md`。

`_sidebar.md` 會由 GitHub Actions 自動產生。

如果本機 push 被拒絕，通常是因為遠端 `_sidebar.md` 已被 GitHub Actions 更新。

解法：

```bash
git pull --rebase origin main
git push
```

---

# 七、完整檔案內容

---

## 1. `index.html`

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <title>我的閱讀筆記</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- Docsify 基礎樣式 -->
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css" />

  <!-- 深色程式碼高亮主題 -->
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/prism-themes@1/themes/prism-one-dark.css" />

  <style>
    :root {
      --theme-color: #2b7a78;
      --base-font-size: 16px;
      --content-max-width: 980px;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI",
        "Noto Sans TC", "Microsoft JhengHei", sans-serif;
    }

    .markdown-section {
      max-width: 980px;
      line-height: 1.8;
    }

    .markdown-section pre {
      background: #1e1e1e !important;
      border-radius: 8px;
      padding: 1rem;
    }

    .markdown-section code {
      font-family: "JetBrains Mono", "Fira Code", Consolas, monospace;
    }

    .sidebar {
      font-size: 15px;
    }
  </style>
</head>

<body>
  <div id="app">載入閱讀筆記中...</div>

  <script>
    window.$docsify = {
      name: "我的閱讀筆記",
      repo: "",
      homepage: "README.md",

      loadSidebar: true,
      subMaxLevel: 3,
      auto2top: true,

      search: {
        maxAge: 86400000,
        paths: "auto",
        placeholder: "搜尋筆記",
        noData: "找不到相關內容",
        depth: 4
      },

      latex: {
        inlineMath: [["$", "$"], ["\\(", "\\)"]],
        displayMath: [["$$", "$$"]]
      }
    };
  </script>

  <!-- Docsify -->
  <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>

  <!-- 搜尋 -->
  <script src="//cdn.jsdelivr.net/npm/docsify@4/lib/plugins/search.min.js"></script>

  <!-- LaTeX -->
  <script src="//cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify-latex@0"></script>

  <!-- Prism 額外語言支援 -->
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-c.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-cpp.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-python.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-javascript.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-css.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-markup.min.js"></script>
</body>
</html>
```

---

## 2. 根目錄 `README.md`

```md
# 📚 個人閱讀筆記

歡迎來到我的閱讀與技術筆記網站。

這個網站使用 **Docsify + GitHub Pages** 建置，以 Markdown 作為主要內容格式，記錄學習、閱讀與整理過程。

---

## ✨ 網站特色

- Markdown 撰寫
- Docsify 即時渲染
- GitHub Pages 自動部署
- 支援程式碼高亮
- 支援 LaTeX 數學公式
- 主題式分類整理
- 自動產生側邊欄目錄

---

## 📂 主題分類

### Markdown

Markdown 語法、文件設計、知識管理與技術寫作。

### Programming

程式設計與計算機基礎。

### STEM

電子、控制、感測器與嵌入式系統。

### Google Apps Script

雲端自動化與 Apps Script 筆記。

### Science

數學與自然科學筆記。

### Poetry

古詩詞、文學閱讀與個人作品整理。

---

## 📝 筆記原則

1. 重理解，不背誦
2. 重脈絡，不只摘錄
3. 持續修訂
4. 保持簡潔
5. 使用 Markdown 長期保存

---

開始閱讀 →
```

---

## 3. `.nojekyll`

```txt
```

這是一個空檔案。

用途：關閉 GitHub Pages 的 Jekyll 處理，避免 `_sidebar.md` 被忽略。

---

## 4. `.gitignore`

```gitignore
.DS_Store
node_modules/
package-lock.json
```

---

## 5. `package.json`

```json
{
  "devDependencies": {
    "docsify-tools": "^1.0.20"
  }
}
```

---

## 6. `.github/workflows/update-sidebar.yml`

```yaml
name: Auto Update Docsify Sidebar

on:
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  sidebar:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install
        run: npm install

      - name: Generate Sidebar
        run: npx docsify-auto-sidebar -d .

      - name: Commit
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com

          git add _sidebar.md

          git diff --cached --quiet || (
            git commit -m "auto update sidebar"
            git push
          )
```

---

## 7. `_sidebar.md`

此檔案會自動產生。

原則上不要手動維護。

若需要初始版本，可使用：

```md
* [首頁](/)

* [Markdown](markdown/README.md)

* [Poetry](poetry/README.md)

* [Programming](programming/README.md)

* [Science](science/README.md)

* [STEM](stem/README.md)

* [Google Apps Script](gas/README.md)
```

之後交給 GitHub Actions 自動更新。

---

## 8. `markdown/README.md`

````md
# Markdown

> 一種用純文字建立知識、文件與出版內容的方法。

---

## 📚 主題定位

這裡不是單純記錄 Markdown 語法。

而是整理：

- Markdown 語法
- 文件設計
- 知識管理
- 技術寫作
- 文件工程
- 發布與部署

目標是建立：

> Write once, publish anywhere.

---

# 為什麼使用 Markdown

Markdown 的核心價值：

- 易讀
- 易寫
- 易維護
- 可版本控制
- 跨平台
- 可長期保存

適合：

- 閱讀筆記
- 教材整理
- 技術文件
- 教案
- 科展紀錄
- 部落格
- GitHub Pages
- Docsify

---

# 學習路線

## 第一章：Markdown 基礎

- 歷史
- 設計理念
- Parser
- Renderer
- 與 HTML 關係

---

## 第二章：完整語法

- 標題
- 段落
- 換行
- 強調
- 清單
- 引用
- 表格
- 圖片
- 超連結
- 腳註

---

## 第三章：技術文件寫作

- 文件架構
- 教材設計
- 長文規劃
- TOC

---

## 第四章：進階功能

- 程式碼區塊
- Syntax Highlight
- LaTeX
- Mermaid
- 引用管理

---

## 第五章：Markdown 生態系

- CommonMark
- GFM
- Markdown Extra
- Docsify
- Obsidian
- Pandoc
- Typora
- Jekyll

---

# 文件範例

## 程式碼

```python
print("Hello Markdown")
````

## 數學公式

行內公式：

$a^2+b^2=c^2$

區塊公式：

$$
E=mc^2
$$

---

# 最終目標

完成本主題後：

* 能使用 Markdown 建立知識庫
* 能撰寫長篇教材
* 能部署閱讀網站
* 能建立可維護文件系統

---

開始閱讀 →

````

---

## 9. `poetry/README.md`

```md
# 古詩詞

> 以閱讀、理解、賞析與整理，重新認識古典文學。

---

## 📚 主題定位

這裡整理：

- 古詩
- 古詞
- 文言文閱讀
- 文學賞析
- 個人閱讀筆記
- 既有創作與作品整理

不是背誦集。

希望透過閱讀與書寫，看見文字背後的時代、情感與思想。

---

# 閱讀方式

建議順序：

1. 先閱讀原文
2. 理解字詞與背景
3. 賞析結構與意境
4. 記錄心得與聯想
5. 延伸閱讀

---

# 分類目錄

## 唐詩

- 五言古詩
- 七言古詩
- 五言律詩
- 七言律詩
- 絕句

---

## 宋詞

- 婉約派
- 豪放派

---

## 元曲

- 散曲
- 雜劇

---

## 文言文

- 古文閱讀
- 名篇整理
- 語句摘錄

---

## 個人作品

- 已完成作品
- 創作草稿
- 修訂版本
- 發表紀錄

---

# 閱讀紀錄格式

```md
# 題目

作者：

朝代：

---

## 原文

內容

---

## 字詞整理

內容

---

## 白話翻譯

內容

---

## 結構分析

內容

---

## 意境與賞析

內容

---

## 延伸閱讀

內容

---

## 個人筆記

內容
````

---

# 精選摘錄

> 文章合為時而著，歌詩合為事而作。

---

> 腹有詩書氣自華。

---

> 讀書破萬卷，下筆如有神。

---

# 待整理清單

* [ ] 唐詩
* [ ] 宋詞
* [ ] 元曲
* [ ] 文言文
* [ ] 個人作品整理
* [ ] 閱讀札記

---

開始閱讀 →

````

---

## 10. `programming/README.md`

```md
# Programming

程式設計與計算機基礎筆記。

---

## 主題方向

- C
- C++
- Assembly
- Python
- Shell
- Web

---

## 筆記目標

- 整理語法
- 記錄範例
- 建立概念
- 保存實作經驗
````

---

## 11. `stem/README.md`

```md
# STEM

電子、控制、感測器與嵌入式系統筆記。

---

## 主題方向

- Arduino
- ESP8266
- ESP32
- 8051
- LinkIt 7697
- Sensors

---

## 筆記目標

- 記錄電路
- 整理實驗
- 保存程式
- 建立教學材料
```

---

## 12. `science/README.md`

```md
# Science

數學與自然科學筆記。

---

## 主題方向

- 數學
- 自然科學
- 科學探究
- 科展紀錄

---

## 筆記目標

- 整理概念
- 保存解題過程
- 記錄觀察
- 建立教學素材
```

---

## 13. `gas/README.md`

```md
# Google Apps Script

Google Apps Script 與雲端自動化筆記。

---

## 主題方向

- Spreadsheet 自動化
- Google Forms
- Google Drive
- Gmail
- Calendar
- API 串接

---

## 筆記目標

- 保存常用程式碼
- 整理自動化案例
- 建立教學與行政工具
```

---

# 八、目前最重要的操作規則

## 1. 新增筆記

```bash
git pull --rebase origin main

# 新增或修改 md 檔案

git add .
git commit -m "add new note"
git push
```

---

## 2. 刪除筆記

```bash
git pull --rebase origin main

rm poetry/test.md

git add .
git commit -m "remove test note"
git push
```

---

## 3. 若 push 被拒絕

看到：

```txt
rejected main -> main (fetch first)
```

解法：

```bash
git pull --rebase origin main
git push
```

---

## 4. 若 GitHub Actions 失敗

到：

```txt
GitHub
→ Actions
→ Auto Update Docsify Sidebar
```

點進紅色失敗項目，看是哪一步錯。

常見錯誤：

* YAML 多了 Markdown 的 ```
* 縮排錯誤
* package.json 不存在
* 權限未開 contents: write

---

# 九、完成狀態

目前網站架構已完成。

你之後只需要專心做三件事：

```txt
寫 Markdown
↓
git push
↓
等待 GitHub 自動更新網站
```

整體流程已經可正式使用。

---

# 十、補充

日後重要習慣（避免 95% 問題）

**開始工作：**

```bash
git pull --rebase origin main
```

**結束：**

```bash
git add .

git commit -m "描述"

git push
```

##### 範例：修正單一檔案內容（poerty/README.md）

```bash
git add .

git commit -m "修正：poerty/README.md"

git push
```
出現錯誤訊息：

```bash
rejected
(fetch first)
```

原因：GitHub Actions 已先更新 _sidebar.md，remote 端多了 commit 動作，目前系統狀態：

    origin/main
    A─B─C

    local
    A─B─D

解決解法：

> 1. 不要重新 commit，直接執行同步：`git pull --rebase origin main`
> 2. 再推：`git push`

##### 範例：專案最佳工作流

🌐 新增

```bash
git pull --rebase origin main
git add .
git commit
git push
```

🌐 修改：

```bash
git pull --rebase origin main
git add .
git commit
git push
```

🌐 改名：

```bash
git pull --rebase origin main
git mv 舊檔 新檔
git commit
git push
```

🌐 刪除：

```bash
git pull --rebase origin main
rm 檔案
git add .
git commit
git push
```

因為你現在有：

    本機
    +
    GitHub Actions（自動_sidebar）

所以先 `pull --rebase` 已經變成`必須的固定習慣`了。