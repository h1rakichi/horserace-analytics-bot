# Website — 馬研アカデミー ポータルサイト

GitHub Pages でホスティングされるメンバー向けポータルサイトのソースファイル一覧です。

**公開URL**: https://h1rakichi.github.io/horserace-analytics-bot/

---

## ファイル構成

```
Website/
├── index.html          # トップページ（ポータル）
├── guide.html          # エンドユーザー向け操作マニュアル
├── policy.html         # ポリシー・免責事項
│
├── 01_tickets.html     # 【入門】JRAの馬券の種類と買い方ガイド
├── 02_expectation.html # 【重要】勝ち続けるための「控除率と期待値」
├── 03_overview.html    # 【概観】競馬の全体像と日本競馬の歴史
├── 04_thoroughbred.html# 【基礎】サラブレッドとは何か？
├── 05_pedigree_1.html  # 【血統①】血統表の読み方入門
├── 06_pedigree_2.html  # 【血統②】配合の考え方（インブリードとニックス）
│
└── 競馬フォーラム/      # 各記事のMarkdownドラフト（原稿管理用）
    ├── 00_競馬スタディ フォーラム構成案.md
    ├── 01_【入門】JRAの馬券の種類と買い方ガイド.md
    ├── 02_【重要】勝ち続けるための「控除率と期待値」.md
    ├── 03_【概観】競馬の全体像と日本競馬の歴史.md
    ├── 04_【基礎】サラブレッドとは何か？.md
    ├── 05_【血統①】血統表の読み方入門.md
    └── 06_【血統②】配合の考え方（インブリードとニックス）.md
```

---

## デザインシステム

全ページ共通の設計方針：

| 要素 | 仕様 |
|------|------|
| CSSフレームワーク | Tailwind CSS（CDN）|
| アイコン | Font Awesome 6.0 |
| カラー | `turf: #2E8B57`（芝グリーン）/ `dark: #1F2937`（ダーク）|
| ナビ | 固定ヘッダー（← ポータルへ戻る + ページ識別）|
| フォント | Helvetica Neue / Hiragino Kaku Gothic ProN / Meiryo |
| フッター | ダーク背景 + turf アクセント + 動的年号 |

### ページ別ヒーロー色

| ページ | グラデーション |
|--------|--------------|
| 01_tickets | グリーン（入門） |
| 02_expectation | アンバー（重要） |
| 03_overview | インディゴ（歴史） |
| 04_thoroughbred | パープル（生物学） |
| 05_pedigree_1 | ティール（血統） |
| 06_pedigree_2 | ローズ（上級） |
| policy | グレー（法的） |

---

## 記事間ナビゲーション

全フォーラム記事はStep 1〜6で連続して読み進められる前後ナビを実装。

```
01_tickets → 02_expectation → 03_overview → 04_thoroughbred → 05_pedigree_1 → 06_pedigree_2
```

06_pedigree_2 の「次へ」はポータルトップ（index.html）に戻る。

---

## 更新手順

1. Markdownドラフト（`競馬フォーラム/*.md`）を編集
2. 対応HTMLファイルをリライト
3. `git add` → `git commit` → `git push origin master`
4. GitHub Pages が自動デプロイ（通常1〜2分）
