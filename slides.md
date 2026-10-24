---
marp: true
theme: default
paginate: true
style: |
  :root {
    --navy: #1A2E4A;
    --blue: #2D6A9F;
    --sky: #5B9EC9;
    --light: #E8F1F8;
    --orange: #E07B3A;
    --body: #334155;
    --gray: #64748B;
  }

  section {
    font-family: 'Hiragino Sans', 'Yu Gothic UI', 'Meiryo', sans-serif;
    background: #ffffff;
    color: var(--body);
    padding: 50px 64px 40px;
    font-size: 20px;
  }

  h1 {
    color: var(--navy);
    font-size: 1.6em;
    border-bottom: 3px solid var(--blue);
    padding-bottom: 10px;
    margin-bottom: 28px;
  }

  h2 {
    color: var(--blue);
    font-size: 1.05em;
    margin-top: 28px;
    margin-bottom: 6px;
  }

  ul { padding-left: 1.3em; line-height: 2.0; margin: 0; }
  li { margin-bottom: 2px; }

  strong { color: var(--navy); }
  em { color: var(--orange); font-style: normal; }

  p { line-height: 1.75; margin: 8px 0; }

  table {
    width: 100%; border-collapse: collapse;
    font-size: 0.88em; margin-top: 16px;
  }
  th { background: var(--navy); color: white; padding: 9px 14px; text-align: left; }
  td { padding: 8px 14px; border-bottom: 1px solid #dde6f0; }
  tr:nth-child(even) td { background: var(--light); }

  blockquote {
    border-left: 4px solid var(--orange);
    background: #fffbf0;
    margin: 20px 0 0;
    padding: 12px 18px;
    border-radius: 0 8px 8px 0;
    font-style: normal;
    font-size: 0.9em;
  }

  code {
    background: #f0f4fa;
    color: var(--navy);
    padding: 2px 6px;
    border-radius: 4px;
    font-size: 0.85em;
  }

  pre {
    background: #f0f4fa;
    border-radius: 8px;
    padding: 16px 20px;
    font-size: 0.78em;
    line-height: 1.7;
  }

  section.title {
    background: var(--navy); color: white;
    display: flex; flex-direction: column; justify-content: center;
  }
  section.title h1 {
    color: white; border-bottom: 3px solid var(--orange);
    font-size: 2em; margin-bottom: 20px;
  }
  section.title p { color: #a0b8d0; margin: 4px 0; }

  section.divider {
    background: var(--navy); color: white;
    display: flex; flex-direction: column; justify-content: center;
  }
  section.divider h1 {
    color: white; border-bottom: 3px solid var(--orange);
    font-size: 2em;
  }
  section.divider p { color: var(--sky); font-size: 1.05em; margin-top: 12px; }

  section.summary {
    background: var(--navy); color: white;
  }
  section.summary h1 { color: white; border-bottom: 3px solid var(--orange); }
  section.summary ul { color: #cfe0f0; line-height: 2.2; }
  section.summary strong { color: white; }
  section.summary .fin {
    background: rgba(224,123,58,0.3);
    border-radius: 10px;
    padding: 14px 20px;
    margin-top: 28px;
    color: white;
    font-weight: bold;
    text-align: center;
    font-size: 0.95em;
  }
---

<!-- _class: title -->

# 開発プロセスと<br>ソフトウェア開発技術

新入社員研修　｜　60 分

開発支援部門

---

# アジェンダ

| 時間 | テーマ |
|------|--------|
| 7分  | ① ソフトウェアはなぜ壊れるのか |
| 18分 | ② 開発プロセスの全体像 |
| 18分 | ③ 開発技術の基礎 |
| 7分  | ④ 品質とプロセスの関係 |
| 5分  | ⑤ 現場で活躍するために |
| 5分  | ⑥ Q&A |

---

<!-- _class: divider -->

# SECTION 01
## ソフトウェアはなぜ壊れるのか

---

# 機械部品 vs. ソフトウェア

|  | 機械部品 | ソフトウェア |
|--|---------|------------|
| 劣化 | 摩耗・変形が目に見える | *劣化しない。バグは最初から潜在* |
| 不具合の原因 | 物理的な破損・疲労 | **思い込み・伝達ミス・仕様の曖昧さ** |
| 変更の影響 | 部品・金型の作り直し | 見えない範囲に波及する |

> ソフトウェア開発には **「プロセス」と「技術」の両輪** が品質を決める

---

# 組込みソフトならではの難しさ

- **ハードと一緒に動く** — センサ・モータ・マイコンを直接制御する
- **時間の制約** — *決められた時間内に応答できなければ「故障」*
- **限られた資源** — メモリ・CPU に余裕がない
- **実機がないと確認しきれない** — 机上では見えない不具合がある
- **出荷後に直しにくい** — 市場に出たら回収・リコールになりうる

> だから **早い段階で・確実に確認する仕組み** が必要になる

---

<!-- _class: divider -->

# SECTION 02
## 開発プロセスの全体像

バグを生む「伝達ミス・思い込み」を防ぐ仕組みとはどういうものか



---

# 要件が伝わらないと何が起きるか

<!-- 画像: images/swing.png を後で追加 -->

> 全員が「ブランコを作る」つもりだった

---

# 開発プロセスとは

> 伝達ミスと思い込みが品質を壊さないよう、**合意と確認**を組み込んだ仕組み

- **合意**：何を作るかをチームと確認し、記録してから次へ進む
- **確認**：決めた通りに作れているかをレビューとテストで検証する

---

# ウォーターフォールモデル

**要件定義 → 基本設計 → 詳細設計 → 実装 → テスト → リリース**

前工程の成果物を確認・承認してから次へ進む。

- 計画・ドキュメントが重視される
- *後になるほど変更コストが大きくなる*
- 組込み・車載開発で主流（A-SPICE、ISO 26262）

> 📐 図面を確定させてから製造に入る — 機械設計と同じ原則

---

# V字モデル

ウォーターフォールの各工程を *設計↔確認の1対1対応* で整理した図

```
要件定義 ───────────────────── 受入テスト
  └─ 基本設計 ─────────── システムテスト
       └─ 詳細設計 ─── 結合テスト
            └─ 実装 ─ 単体テスト
```

↕ **縦**：上位で決めたことが、下位の設計に漏れなく反映されているか
↔ **横**：左で決めたことを、右のテストで 1 対 1 に確かめる

> *「これをどうやって確認するか」が答えられない設計は未完成*

---

# Verification と Validation

|  | Verification（検証） | Validation（妥当性確認） |
|--|-------------------|----------------|
| 問い | **正しく作っているか？** | **正しいものを作っているか？** |
| 比べる相手 | 仕様書・設計書（決めたこと） | 使う人の本当のニーズ・使われ方 |
| 主な手段 | レビュー、単体〜システムテスト | 受入テスト、実車・実環境での評価 |

- V字の縦・横の確認は、ほとんどが **Verification**
- Verification を全部通っても、*仕様そのものがずれていれば意味がない*

> 🔧 図面どおりかの **寸法検査** と、用途に合うかの **実機評価** は別の問い

---

<!-- _class: divider -->

# SECTION 03
## 開発技術の基礎

品質を人間の注意力に頼らないための道具と習慣

---

# 全体地図 — V字のどこで何を使うか

```
要件定義 ──────────────────── 受入テスト（実車・実機）
  └ 基本設計 ─────────── システムテスト（HILS）
      └ 詳細設計 ───── 結合テスト
          └ 実装 ── 単体テスト（自動化ツール）
             └ コーディング規約（MISRA-C）／静的解析

全工程で使う：Git（変更履歴）・レビュー・チケット（変更／不具合管理）・CI
全体の枠組み：A-SPICE（プロセス）／ISO 26262（機能安全）
```

> 全部覚えなくてよい。**聞いたときに「地図のここ」と分かれば十分**

---

# バージョン管理（Git）

```
設計書_最終.xlsx
設計書_最終2.xlsx
設計書_最終_確認済_田中修正.xlsx  ← どれが最新？
```

Gitで解決できること：

- **誰が・いつ・何を・なぜ** 変えたかを自動記録
- 任意の時点に戻せる
- 複数人の変更を安全に統合できる

> 🏭 設変管理台帳が自動化されたもの

---

# テスト — なぜ「書く」のか

テストコードがあると：

- 変更後に**既存機能を壊していないか**確認できる
- 「このコードは何をするか」が読める**仕様書**になる
- *人間が確認を忘れても、機械は忘れない*

**CI** — コードを変更するたびに自動でテストを実行する仕組み

**実機の前に段階的に確かめる**（組込み）

```
SILS（PC上で模擬） → HILS（本物のECU＋模擬した車両） → 実機・実車
```

> バグの発見が遅れるほど修正コストは大きくなる — 製品開発全般に共通する原則

---

# コードレビュー

**書いた本人が見ても、思い込みでミスに気づけない**

レビューで得られること：

- バグの早期発見
- 書き手の意図と読み手の解釈のズレをなくす
- 先輩の設計思想を学ぶ機会

**静的解析** — コーディング規約（*MISRA-C*）違反や危険なパターンを*ツールが自動で*検出

- 機械に任せられるチェックは機械に → 人は **設計の意図** の確認に集中

> コードレビューは「批判」ではなく **「設計の意図を言語化して確認する作業」**

---

<!-- _class: divider -->

# SECTION 04
## 品質とプロセスの関係

道具を使うだけでは足りない。プロセスを守ることが品質を生む。

---

# プロセスが品質を決める

> 工場の SOP（標準作業手順書）と同じ。
> プロセスを標準化すると **「誰がやっても同じ品質」** が出せる。

| 枠組み | 役割 |
|-------|------|
| **A-SPICE** | 車載ソフト開発のプロセス評価モデル |
| **ISO 26262** | 機能安全の国際規格 |
| **CI** | プロセスをツールで自動化する仕組み |

---

# 技術的負債

**今は動く。でも将来、大きなコストになる手抜きの積み重ね。**

- テストを書かない → 後でバグが大量に出る
- コメントを書かない → 1年後に自分でも読めない
- プロセスを省く → 後工程で手戻りが発生する

*金融の借金と同じ。利子がついて膨らみ続ける。*

> プロセスを守ることは **「将来の自分とチームへの投資」**

---

<!-- _class: divider -->

# SECTION 05
## 現場で活躍するために

知識・ツール・プロセスを活かすための考え方

---

# 3つのマインドセット

## 01　再現性を意識する
「なぜ動いたか・なぜ壊れたか」を説明できる状態にする。
説明できない = 次に壊れたとき同じ手順で直せない。

## 02　記録を残す
判断の理由・確認した事実を残す。
*未来の自分とチームへの贈り物。*

## 03　バスファクターを下げる
「自分しか知らない」情報を作らない。

> 🚌 バスファクター：何人いなくなったらプロジェクトが止まるか

---

<!-- _class: summary -->

# まとめ

- 開発プロセス：**合意と確認**を組み込んだ仕組み — これが品質を決める
- バグは **要件・設計の段階** で既に生まれる。組込みは **出荷後に直しにくい**
- V字モデル：**テスト観点が作れない設計は未完成**
- V&V：**仕様どおりか**（Verification）と **本当に役立つか**（Validation）は別の問い
- Git・レビュー・静的解析・テスト・CI は「品質を人間の注意力に頼らない」仕組み
- プロセスを守ることは **技術的負債を作らない長期投資**
- 再現性・記録・チームへの貢献は **「未来の自分を楽にする」** 行動

<div class="fin">
プロセスも技術も、使いながら身につけていきましょう。一緒に育てていきます。
</div>

---

<!-- _class: divider -->

# Q & A

ご質問はありますか？
