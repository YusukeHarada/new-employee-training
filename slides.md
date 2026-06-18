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
| 5分  | ① ソフトウェアはなぜ壊れるのか |
| 15分 | ② 開発プロセスの全体像 |
| 20分 | ③ 開発技術の基礎 |
| 10分 | ④ 品質とプロセスの関係 |
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

<!-- _class: divider -->

# SECTION 02
## 開発プロセスの全体像

---

# ウォーターフォールモデル

**要件定義 → 基本設計 → 詳細設計 → 実装 → テスト → リリース**

前工程の成果物を確認・承認してから次へ進む。

- 計画・ドキュメントが重視される
- *後になるほど変更コストが大きくなる*
- 組込み・車載開発で主流（A-SPICE、ISO 26262）

> 📐 図面を確定させてから製造に入る — 機械設計と同じ原則

---

# アジャイル開発

短いサイクル（**スプリント**：1〜2週間）で繰り返す。

| 観点 | ウォーターフォール | アジャイル |
|-----|----------------|---------|
| 変更への対応 | 難しい | 得意 |
| 向いている開発 | 要件が固定 | 要件が変化・不確か |
| ドキュメント | 重厚・詳細 | 必要最小限 |

- 組込み開発はウォーターフォールが主流
- *「小さく試して早く確認する」考え方は現場でも活きる*

---

# V字モデル

ウォーターフォールの各工程を *設計↔確認の1対1対応* で整理した図

```
要件定義 ───────────────────── 受入テスト
  └─ 基本設計 ─────────── システムテスト
       └─ 詳細設計 ─── 結合テスト
            └─ 実装 ─ 単体テスト
```

↕ **縦（Verification）**：上位設計が下位設計に正しく反映されているか
↔ **横（Validation）**　：設計と検証が 1 対 1 で対応しているか

> *「これをどうやって確認するか」が答えられない設計は未完成*

---

# Verification と Validation

|  | Verification（縦） | Validation（横） |
|--|-------------------|----------------|
| 問い | **正しく作っているか？** | **正しいものを作っているか？** |
| 確認方法 | レビュー・トレーサビリティマトリクス | テスト（実際に動かす） |

- Verification だけ通っても、*作るものが間違っていれば意味がない*

> だから **縦と横、両方のトレーサビリティ** で品質を担保する

---

<!-- _class: divider -->

# SECTION 03
## 開発技術の基礎

品質を人間の注意力に頼らないための道具と習慣

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

**CI/CD** — コードを変更するたびに自動でテストを実行する仕組み

> バグの発見が遅れるほど修正コストは大きくなる。
> この原則はソフトウェアに限らず製品開発全般に共通する。

---

# コードレビュー

**書いた本人が見ても、思い込みでミスに気づけない**

レビューで得られること：

- バグの早期発見
- 書き手の意図と読み手の解釈のズレをなくす
- コーディング規約（*組込みでは MISRA-C* など）の確認
- 先輩の設計思想を学ぶ機会

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
| **CI/CD** | プロセスをツールで自動化する仕組み |

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

- バグは **要件・設計の段階** で既に生まれる
- V字モデル：**テスト観点が作れない設計は未完成**
- V&V：縦（Verification）と横（Validation）、**両方のトレーサビリティ**で品質を担保
- Git・テスト・CI/CD は「品質を人間の注意力に頼らない」仕組み
- プロセスを守ることは **技術的負債を作らない長期投資**
- 再現性・記録・チームへの貢献は **「未来の自分を楽にする」** 行動

<div class="fin">
プロセスも技術も、使いながら身につけていきましょう。一緒に育てていきます。
</div>

---

<!-- _class: divider -->

# Q & A

ご質問はありますか？
