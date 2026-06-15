# 🦙 Ollama 快速導覽

> 在自己的電腦上執行大型語言模型（LLM），建立可控制、可離線、可延伸的個人 AI 工作環境。

---

## 📚 主題定位

這裡整理：

* Ollama 基礎概念
* 本地端 AI（Local AI）
* 大型語言模型（LLM）
* 模型下載與管理
* Prompt 設計
* API 呼叫
* 與程式整合
* 教學與應用案例

不是單純安裝教學。

希望建立：

> 自己可掌控、可重現、可持續累積的 AI 工作環境。

---

# 為什麼使用 Ollama

雲端 AI 很方便，但本地模型有不同價值：

* 離線可用
* 資料不離開電腦
* 不受 API 次數限制
* 可切換模型
* 可自行微調流程
* 適合實驗與教學

適合：

* 個人知識庫
* 技術研究
* AI 教學
* 程式輔助
* 文件整理
* 科展專題
* 本地助理

---

# 學習路線

---

## 第一章：認識 Ollama

整理：

* Ollama 是什麼
* 與 ChatGPT 差異
* Ollama 架構
* 模型概念（Model）
* Token 概念
* Context Window

預計內容：

* 安裝
* 啟動
* 第一個模型

---

## 第二章：基本操作

整理：

* CLI 指令
* 啟動模型
* 模型管理
* 匯出與刪除

預計內容：

```bash
ollama run llama3
```

```bash
ollama list
```

```bash
ollama pull
```

```bash
ollama rm
```

---

## 第三章：常用模型整理

整理：

* Llama
* Gemma
* Qwen
* DeepSeek
* Mistral
* Phi

比較：

* 模型大小
* 中文能力
* 程式能力
* 推理速度
* 記憶體需求

---

## 第四章：API 與整合

整理：

* HTTP API
* Python 呼叫
* Shell
* JavaScript
* Apps Script

預計：

```python
import requests
```

```js
fetch()
```

---

## 第五章：知識庫與文件系統

整理：

* Markdown × Ollama
* RAG
* 向量資料庫
* 本地知識管理

應用：

* 教材整理
* 閱讀筆記
* 教案產生

---

## 第六章：進階應用

整理：

* WebUI
* Docker
* Open WebUI
* AnythingLLM
* 自建聊天系統

---

# 常用指令速查

查看版本：

```bash
ollama --version
```

啟動：

```bash
ollama run llama3
```

查看模型：

```bash
ollama list
```

下載模型：

```bash
ollama pull qwen3
```

刪除模型：

```bash
ollama rm llama3
```

停止：

```bash
/bye
```

---

# 筆記紀錄格式

建議：

```md
# 主題

日期：

模型：

版本：

---

## 目的

---

## 操作過程

---

## 輸入 Prompt

---

## 輸出結果

---

## 問題紀錄

---

## 優化方向

---

## 個人心得
```

---

# 待整理清單

* [ ] 安裝教學
* [ ] CLI 指令
* [ ] 模型管理
* [ ] Prompt 工程
* [ ] API
* [ ] Docker
* [ ] RAG
* [ ] 教學應用
* [ ] 本地 AI 工作流

---

# 最終目標

完成本主題後：

* 能獨立架設 Ollama
* 能管理本地模型
* 能整合程式與 API
* 能建立自己的 AI 工作環境

---

開始閱讀 →
