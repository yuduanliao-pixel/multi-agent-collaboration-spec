# 多代理 AI 協作制度規格書
**Multi-Agent AI Collaboration Framework — a field-tested governance spec**

**繁體中文**(原文)｜ **English** (translation) — both maintained in this repo.

一套在單機上真實運轉的多代理 AI 協作制度:角色分離、檔案協調、審查閘門、治理記憶、排程自動化。
本規格書不是理論設計——文中所有制度與教訓,均來自一套實際系統(兩個 AI 編碼代理＋一個訊息閘道代理＋一位使用者)的運轉覆盤。

A multi-agent AI collaboration framework running in real production on a single PC: role separation, file-based coordination, review gates, governed memory, scheduled automation. Nothing here is theoretical — every rule and every lesson is a post-mortem from a live system (two AI coding agents + one messaging-gateway agent + one user).

## 內容 / Contents

| 語言 / Language | Markdown | PDF (A4) |
|---|---|---|
| 繁體中文(原文) | [multi-agent-collaboration-spec.md](multi-agent-collaboration-spec.md) | [PDF,11 頁](multi-agent-collaboration-spec.pdf) |
| English | [multi-agent-collaboration-spec.en.md](multi-agent-collaboration-spec.en.md) | [PDF, 13 pages](multi-agent-collaboration-spec.en.pdf) |

## v1.2(2026-06-13)更新 / What's new

- **車道閘門:角色界線變成代碼 / Lane guard — the role boundary as code** — 不再只是叮嚀;設計/審查代理被**寫前閘門**擋住、不得編輯實作端產品碼,而**緊急通道由風險門檻代碼驗證**(高風險,或中風險但會直接導致系統卡死/構成資安風險)。A pre-write gate, not a reminder, with a risk-gated emergency override.
- **車道邊界納入設計階段 / Lane boundary defined at design time** — 新專案先定義風險、再註冊進閘門清單,絕不留未保護的產品庫。
- **雙向自治閉環 / The bidirectional autonomy loop, closed** — 事件驅動派工＋嚴格有界 worker(寫入限自身資料夾、shell 限驗證、無網路)＋遞迴護欄(代理不得自動改自己的審批機制)＋演習啟用。Event-driven dispatch, a strictly bounded worker, a recursion guard, and activation-by-drill.
- **教訓擴充至九則 / Lessons → nine** — 不信報告,連自己的檢查也不信。

## v1.1(2026-06-12)更新 / Earlier

- **審查庭與判例制度 / The Review Court & precedent system** — reviews that learn from reviews: significant rulings are distilled into governed precedents, pre-read before every future review (Reflexion, institutionalized)
- **Token 經濟三層階梯 / Three-tier token economy** — starvation forbidden, compression is the floor, refinement is the direction: judgment-per-token rises with accumulation
- **認領機制 / Claim & lease** — agents stamp a claim before processing any task folder; grabbing the wrong letter becomes mechanically impossible
- **階段閘門實戰 / Stage gates, field-tested** — including the overnight incident where an AI refused to bypass its own gate with nobody watching
- **教訓 6 → 8 則 / Lessons 6 → 8** — self-referential tooling changes; the fix for a lesson is itself an untested path

## 三條公理 / Three axioms

1. **球員不兼裁判 / Players don't referee** — 設計審查的 AI 不寫生產程式碼;實作的 AI 不驗收自己的交付。
2. **檔案是唯一真相 / Files are the single source of truth** — 所有協調走 append-only 純文字檔,不依賴任何一方的對話記憶。
3. **閘門必須寫進代碼 / A gate exists only where code enforces it** — 「需要批准」如果只寫在文件裡,而排程器跑著上膛的代碼,批准就已經被繞過了。

## 適合誰 / Who is this for

- 同時使用多個 AI 編碼工具(Claude、Codex 等),受夠了在它們之間人肉傳話的人
- 想給 AI 產出加上「獨立審查 + 放行門檻」品質迴圈的團隊
- 對「AI 長期記憶該如何治理」「AI 審查如何隨案例變強」有興趣的人

Anyone running multiple AI coding tools who is tired of being the human message relay; teams that want an independent-review quality loop on AI output; anyone curious how AI long-term memory should be governed — and how AI reviews can grow stronger with every case.

## 讓你的 AI 幫你導入 / Let your AI set it up

如果你使用具備檔案讀寫能力的 AI 編碼助手(Claude Code、Codex CLI 等),
把下面這段連同本 repo 網址一起貼給它,它就能直接為你搭好最小可行版本:

```text
請閱讀這份規格書:
https://github.com/yuduanliao-pixel/multi-agent-collaboration-spec/blob/main/multi-agent-collaboration-spec.md

依照第 13 節「最小可行導入」的第一步與第二步,在我的工作目錄建立:
1. coordination/ 資料夾(queue.md、staging/、README.md 格式契約)
2. 一頁審查紀律文件(角色分離、reconcile 流程、固定 rubric 與 80 分放行線、needs_fix 三輪上限)
先給我看你的規劃,經我確認後再動手。建完後示範登記第一個任務。
```

English version — paste this to a file-capable AI coding assistant (Claude Code, Codex CLI, etc.):

```text
Read this spec:
https://github.com/yuduanliao-pixel/multi-agent-collaboration-spec/blob/main/multi-agent-collaboration-spec.en.md

Following Section 13 "Minimal viable adoption" steps 1-2, create in my workspace:
1. a coordination/ folder (queue.md, staging/, README.md format contract)
2. a one-page review discipline doc (role separation, reconcile flow, the fixed rubric with its 80-point pass line, the three-round needs_fix cap)
Show me your plan first; only act after I confirm. Then demonstrate registering the first task.
```

注意:純聊天型 AI(無檔案工具)只能讀懂規格、無法代你建檔;
自動化階段(規格書第 9 節)涉及排程任務與通知管道,建議在 AI 協助下逐項手動確認。

## License

本作品採用 [CC BY 4.0](LICENSE) 授權 — 歡迎轉載、改作、商用,標註出處即可。
Licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/).
