# **研究室『馬研』 システムリポジトリ**

このリポジトリは、競馬を統計と論理でハックするためのクローズドコミュニティ『馬研』の**公式ポータルサイト**および、\*\*競馬秘書Bot（AI予測エンジン）\*\*のソースコードを統合管理しています。

## **🌐 公式ポータルサイト (GitHub Pages)**

LINE公式アカウントと連動する、メンバー向けのアカデミック・ポータルです。

以下のURLからアクセスできます（GitHub Pagesにて自動ホスティングされています）。

**👉 [https://h1rakichi.github.io/horserace-analytics-bot/](https://h1rakichi.github.io/horserace-analytics-bot/)**

* **収録コンテンツ:**  
  * 競馬集中講義（血統・期待値・歴史などのマークダウン講義録をHTML化）  
  * システム操作ガイド  
  * ポリシーおよび免責事項  
* **ファイル構成:** リポジトリルートにある \*.html ファイルが該当します。

## **🤖 競馬秘書Bot (Backend System)**

Discord（管理者用ダッシュボード）とLINE公式アカウント（メンバー用UI）で動作する、Python製の競馬予想支援ボットです。TARGET frontier JVのCSVデータをSQLiteに統合し、LLM（Moonshot等）を用いた予測とDB検索を提供します。

### **動作環境・プラットフォーム**

| プラットフォーム | 対象 | 主な機能 |
| :---- | :---- | :---- |
| **Discord** | 管理者（オーナー） | 予測ウィザード・AI相談・学習スナップショット・エラー通知・ユーザー承認 |
| **LINE 公式** | 招待メンバー | 予測・DB検索・収支管理・通知（リッチメニュー操作） |

### **バックエンド・セットアップ手順**

**1\. Python環境の準備 (3.11以上推奨)**

pip install \-r requirements.txt

**2\. 環境変数の設定**

.env.example をコピーして .env を作成し、Discordトークンや各種チャンネルIDを設定します。

**3\. 過去成績データのインポート（初回フルインポート）**

TARGET frontier JV が出力するCSV（成績・レース）を読み込み、DBを構築します。

python scripts/import\_tfjv.py ^  
  \--seiseki-dir "C:\\TFJV\\SEISEKI" ^  
  \--race-dir "C:\\TFJV\\TXT\\レース" ^  
  \--clear \--raw

### **主要ディレクトリ構成**

horserace-analytics-bot/  
├── \*.html               \# ポータルサイト用フロントエンド（GitHub Pages）  
├── bot/                 \# Botアプリケーション本体（Discord Cog, FastAPI）  
│   ├── commands/        \# スラッシュコマンド実装  
│   ├── services/        \# AI・DB・LINE・予測ロジック  
│   └── ui/              \# Discord用ダッシュボードUI  
├── data/                \# SQLite DB, JSON, パネルID（※通常は.gitignore）  
└── scripts/             \# バッチ処理、データインポーター

## **ドキュメント一覧**

開発・運用に関する詳細な仕様は、以下のマークダウンを参照してください。

* ARCHITECTURE.md \- システム構成と予測スコアリングロジック  
* DATA\_SCHEMA.md \- データベース構造  
* COMMANDS.md \- Discordコマンドリファレンス  
* LINE\_GUIDE.md \- LINE公式アカウントの運用と承認フロー  
* HANDOVER.md \- 全体引き継ぎ資料