# Choreia Forms

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/使ってみる-GitHub%20Pages-brightgreen)](https://choreia.github.io/Forms/)

**Google Formsの美しい代替。完全無料・データは自分のもの。**

テーマを選ぶだけで美しいフォームが作れます。AIに「美容院向けの予約フォーム」と伝えれば一発生成。回答はすべてあなたのGoogle Sheetsに直接保存されるため、サーバーにデータを預ける必要はありません。

**[使ってみる](https://choreia.github.io/Forms/)**

## 特徴

- **9種類のテーマ** — ミニマル・ダーク・ラグジュアリー・さくら等、クリックで即切替
- **カラー・フォント・角丸を自由にカスタマイズ** — Google Formsでは不可能なデザイン自由度
- **AI生成** — Googleログインするだけで、自然言語でフォームを一発生成・修正（Gemini連携）
- **Google Sheets連携** — Googleログインだけで自動セットアップ、IDの手入力不要
- **リアルタイムプレビュー** — Desktop / Tablet / Mobile での表示を即座に確認
- **ドラッグ＆ドロップ** — 質問の並び替えが直感的
- **9種類の入力タイプ** — テキスト・メール・電話・長文・ドロップダウン・ラジオ・チェック・日付・数値
- **HTMLエクスポート** — 生成したフォームをHTMLファイルとしてダウンロード、どこにでもデプロイ可能
- **完全無料** — オープンソース（MIT）、回答数無制限、広告なし

## Typeformとの比較

| | Choreia Forms | Typeform | Google Forms |
|---|---|---|---|
| 料金 | **無料** | $25/月〜 | 無料 |
| デザイン自由度 | **カラー・フォント・角丸すべてカスタム** | テンプレートのみ | ほぼなし |
| AI生成 | **自然言語で一発生成** | なし | なし |
| データの場所 | **自分のGoogle Sheets** | Typeformのサーバー | Googleのサーバー |
| 回答数制限 | **無制限** | 10件/月（無料） | 無制限 |
| セルフホスト | **可能（HTML出力）** | 不可 | 不可 |

## アーキテクチャ

```
┌──────────────────┐     ┌───────────────┐
│  ブラウザ         │────▶│ Google Sheets  │
│  (HTML/CSS/JS)   │◀────│ (回答データ)    │
└────────┬─────────┘     └───────────────┘
         │
         ▼
┌──────────────────┐
│  Gemini API      │
│  (AI生成・OAuth)  │
└──────────────────┘
```

- **サーバーレス** — GitHub Pagesで静的ホスティング。バックエンドサーバー不要
- **データ保存** — ユーザーのGoogle Sheetsに直接保存。サーバーにデータを送信しません
- **AI生成** — GoogleログインのOAuthトークンでGemini APIを利用。APIキー不要・運営側のコストはゼロ

## 使い方

1. [https://choreia.github.io/Forms/](https://choreia.github.io/Forms/) にアクセス
2. 「Googleでログイン」→ Google Sheetsが自動でセットアップされます
3. 質問を追加・編集、テーマを選択
4. AIに「〇〇向けフォーム」と指示すればフォームを自動生成（Gemini連携）
5. 「公開する」→ HTMLをダウンロードしてデプロイ

## ローカル開発

```bash
git clone https://github.com/Choreia/Forms.git
cd Forms/web
python3 -m http.server 8080
```

ブラウザで http://localhost:8080 にアクセスしてください。

## プロジェクト構成

```
Forms/
├── web/
│   └── index.html      # フォームビルダー（全機能が1ファイル）
├── .github/
│   └── workflows/
│       └── pages.yml   # GitHub Pages自動デプロイ
├── README.md
└── LICENSE
```

## ロードマップ

| 機能 | 状況 |
|---|---|
| テーマ選択・カラーカスタマイズ | 完了 |
| AI生成（Gemini） | 完了 |
| Google Sheets自動連携 | 完了 |
| リアルタイムプレビュー | 完了 |
| 回答期限・上限設定 | 完了（UI） |
| reCAPTCHA対応 | 予定 |
| 条件分岐（回答による質問の出し分け） | 予定 |
| Google Apps Script連携（サーバーレス回答受付） | 予定 |
| テンプレートギャラリー | 予定 |

## 関連プロジェクト

- [みんなの経理](https://github.com/Choreia/minnano-keiri) — 完全無料の会計ソフト（同じアーキテクチャ）
- [kaikei-rs](https://github.com/Ryujiyasu/kaikei-rs) — 日本の税金計算エンジン（Rust）

## ライセンス

[MIT](LICENSE)
