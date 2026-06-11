# 多代理 AI 協作制度規格書
**Multi-Agent AI Collaboration Framework — a field-tested governance spec**

一套在單機上真實運轉的多代理 AI 協作制度:角色分離、檔案協調、審查閘門、治理記憶、排程自動化。
本規格書不是理論設計——文中所有制度與教訓,均來自一套實際系統(兩個 AI 編碼代理＋一個訊息閘道代理＋一位使用者)的運轉覆盤。

## 內容

- 📄 [規格書全文(Markdown)](multi-agent-collaboration-spec.md)
- 📑 [規格書 PDF(A4,8 頁,含架構圖與流程圖)](multi-agent-collaboration-spec.pdf)

## 三條公理

1. **球員不兼裁判** — 設計審查的 AI 不寫生產程式碼;實作的 AI 不驗收自己的交付。
2. **檔案是唯一真相** — 所有協調走 append-only 純文字檔,不依賴任何一方的對話記憶。
3. **閘門必須寫進代碼** — 「需要批准」如果只寫在文件裡,而排程器跑著上膛的代碼,批准就已經被繞過了。

## 適合誰

- 同時使用多個 AI 編碼工具(Claude、Codex 等),受夠了在它們之間人肉傳話的人
- 想給 AI 產出加上「獨立審查 + 放行門檻」品質迴圈的團隊
- 對「AI 長期記憶該如何治理」有興趣的人

## 快速導入

規格書第 11 節提供三步起步法:十分鐘建檔案協調層 → 半天立審查紀律 → 漸進自動化。
前兩步不需要寫任何程式碼。

## 讓你的 AI 幫你導入

如果你使用具備檔案讀寫能力的 AI 編碼助手(Claude Code、Codex CLI 等),
把下面這段連同本 repo 網址一起貼給它,它就能直接為你搭好最小可行版本:

```text
請閱讀這份規格書:
https://github.com/yuduanliao-pixel/multi-agent-collaboration-spec/blob/main/multi-agent-collaboration-spec.md

依照第 11 節「最小可行導入」的第一步與第二步,在我的工作目錄建立:
1. coordination/ 資料夾(queue.md、staging/、README.md 格式契約)
2. 一頁審查紀律文件(角色分離、reconcile 流程、80 分放行線、needs_fix 規則)
先給我看你的規劃,經我確認後再動手。建完後示範登記第一個任務。
```

注意:純聊天型 AI(無檔案工具)只能讀懂規格、無法代你建檔;
自動化階段(規格書第 8 節)涉及排程任務與通知管道,建議在 AI 協助下逐項手動確認。

## License

本作品採用 [CC BY 4.0](LICENSE) 授權 — 歡迎轉載、改作、商用,標註出處即可。
Licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).

---

*規格書為繁體中文。The spec is written in Traditional Chinese; the architecture diagrams (Mermaid) are language-light and self-explanatory.*
