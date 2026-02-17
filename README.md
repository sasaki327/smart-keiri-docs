# SMART KEIRI｜スマート経理

![Python](https://img.shields.io/badge/Python-3.11%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.x-092E20?style=for-the-badge&logo=django&logoColor=white)
![Gemini](https://img.shields.io/badge/AI-Gemini_3.0_Flash-8E75B2?style=for-the-badge&logo=google&logoColor=white)
![Status](https://img.shields.io/badge/Status-In_Production-success?style=for-the-badge)

> **⚠️ Note: This repository contains documentation only.**
>
> 本レポジトリは、**SMART KEIRI** の仕様・設計思想・リリースノートを公開するためのドキュメント用レポジトリです。
> ソースコード本体は、セキュリティおよび商用ライセンスの都合上、Privateレポジトリにて厳重に管理・運用されています。
>
> 導入のご相談やデモ環境の試用については、[Wantedlyプロフィール](ここにあなたのWantedlyのURLを貼ってください) 経由でお問い合わせください。

---

## 📖 サービス概要

**SMART KEIRI（スマート経理）** は、従業員10〜50名規模の中小企業を対象とした、**シングルテナント型** の経費精算・承認ワークフローシステムです。

「ITが苦手な人」がつまずかないことを最優先した **OJI-UX（おじさまUX）** を採用し、最新の **Google Gemini 3.0 Flash** を活用した領収書解析（OCR）と、国税庁API連携によるインボイス監査機能を統合しています。

### コンセプト：現場で止まらないUX
大手SaaSのような多機能さではなく、**「経理1名・社長兼務」** の現場で、月末の事務作業を確実に終わらせるための「迷わない仕組み」を提供します。

---

## 🚀 主な機能 (Features)

### ✨ AI 領収書解析 (Gemini 3.0 Flash OCR)
- **超高速OCR**: 最新の LLM (`Gemini 3.0 Flash`) を採用し、画像から**金額・日付・支払先・インボイス番号**を即座に抽出。
- **スマート税率分割**: 10%と8%（軽減税率）が混在するレシートを自動計算し、内訳を自動入力。
- **AI 信頼度スコア**: AIがどれだけ自信を持って読み取ったかを可視化し、人間が確認すべき箇所をナビゲート。

### ⚖️ 法制度・コンプライアンス対応
- **インボイス制度 (国税庁API連携)**:
    - 読み取ったT番号（登録番号）を国税庁データベースとリアルタイム照合。
    - **「実在する番号か」「事業者名は合っているか」** を自動検証し、なりすましや入力ミスを防止。
- **電子帳簿保存法**:
    - 訂正・削除の履歴（監査ログ）を完全記録。
    - **月次締め機能** により、確定した過去データの改ざんをシステムレベルでロック。

### 📱 究極のモバイル体験 (OJI-UX)
- **OJI-UX Toggle (おじさまスイッチ)**:
    - ワンタップで「標準表示」と「超拡大表示（老眼対応）」を切り替え。
    - 独自の巨大フォント設計とコントラスト調整により、裸眼での視認性を確保。
- **スマホ専用撮影モード**: ブラウザからカメラを直接起動し、撮影→解析→申請までを最短フローで完結。

### 🛡 堅牢なインフラ・セキュリティ
- **シングルテナント構成**: 顧客ごとに**独立したVPS・DB・ストレージ**を構築。他社の障害や負荷の影響を受けません。
- **死活監視 & 自動バックアップ**: `/health_check` エンドポイントによる常時監視と、日次バックアップ・復元テスト体制。

---

## 📂 System Architecture

堅牢な Django プロジェクト構成を採用し、機能ごとにアプリケーションを疎結合に分割しています。

```text
smart-keiri/
├── config/             # プロジェクト設定・ミドルウェア (Settings)
├── expenses/           # 経費精算コアロジック (Domain Layer)
│   ├── models/         # 申請・承認・履歴管理モデル
│   ├── services/       # Gemini AI解析・国税庁API連携ロジック
│   └── views/          # OJI-UX 実現のためのView層
├── accounts/           # 認証・ユーザー管理・プロフィール
├── templates/          # OJI-UX フロントエンドテンプレート
├── static/             # 静的ファイル (CSS/JS/Chart.js)
├── requirements.txt    # 依存ライブラリ (google-genai, pillow, psycopg2等)
└── .env.example        # 環境変数定義 (APIキー・テーマ設定)
```

## 🛠 技術スタック (Tech Stack)

| Category | Technology |
| :--- | :--- |
| **Backend** | Python 3.11+, Django 5.x |
| **Database** | PostgreSQL (Production), SQLite3 (Demo) |
| **AI / OCR** | **Google Gemini 3.0 Flash** (via `google-genai` SDK) |
| **Gov API** | 国税庁 インボイス制度 適格請求書発行事業者公表システム Web-API |
| **Frontend** | Vanilla JS, CSS (No Framework), Chart.js v4 |
| **Infra** | Linux VPS (Single Tenant), Nginx, Gunicorn |

---

## 📝 Release Notes (History)

### v1.1.9 (2026/02/16)
- **パスワードリセット機能**: 安全なリカバリーフローの実装。
- **UI Hardening**: モバイル環境におけるボタン配置のミリ単位修正。
- **画像回転**: 申請詳細画面からの領収書向き修正機能を追加。

### v1.1.7 (2026/02/14) - Professional Update
- **マスターデータ管理 (CSV)**: 部署・カテゴリー・ユーザーの一括インポート/エクスポート機能。
- **マルチテナント・テーマ**: 環境変数による業種別カラープリセット（医療・建設・ITなど）対応。
- **重複検知アラート**: AI解析時に過去の類似申請（金額・日付・支払先）を検知し警告する機能を強化。
- **弥生会計対応**: `freee` `MoneyForward` に加え、`弥生会計` 形式でのCSVエクスポートを実装。

### v1.1.5 (2026/02/11)
- **インフラ最適化**: サーバーサイドでの画像自動圧縮（WebP/JPEG）によるストレージ効率化（90%削減）。
- **国税庁API連携強化**: T番号からの「正式名称（商号）」自動取得・補完機能を実装。
- **Gemini SDK移行**: 最新の `google-genai` ライブラリへ完全移行。

### v1.1.4 (2026/02/09)
- **OJI-UX Toggle 実装**: モバイル画面での「標準/拡大」即時切替スイッチを搭載。
- **フォント最適化**: `IBM Plex Sans JP` を採用し、視認性を極限まで向上。

### v1.1.0 (2026/02/05)
- **AI Check**: 承認者向けに、申請内容の矛盾をAIが指摘する監査アシスタント機能をリリース。
- **月次締め機能**: 経理担当者による月単位のデータロック機能を実装。

### v1.0.0 (2026/02/03)
- **Initial Release**: サービスローンチ。

---

## 📬 Contact / 導入のご相談

本システムは、設計から運用保守までを一貫して提供する **「顔の見えるSaaS」** です。
運用方針や価格感（初期27万円〜）に共感いただける企業様に向けて、**Wantedly** にて詳細を公開しています。

デモ環境のご案内も可能ですので、下記よりお気軽にご連絡ください。

[👉 **Wantedly プロフィール・お問い合わせはこちら**](ここにあなたのWantedlyのURLを貼ってください)
