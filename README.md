# SMART KEIRI - docs
中小企業の「現場」に特化したAI経費精算SaaS｜Gemini 3.0 Flash搭載 / インボイス・電帳法完全対応 / シングルテナント構成 / Django 5.x &amp; PostgreSQL

# SMART KEIRI（スマート経理）

![Python](https://img.shields.io/badge/Python-3.11%2B-blue)
![Django](https://img.shields.io/badge/Django-5.x-green)
![Gemini](https://img.shields.io/badge/AI-Gemini%203.0%20Flash-orange)
![Status](https://img.shields.io/badge/Status-In%20Production-success)

**「ITが苦手な人」を主役にする、現場特化型のAI経費精算SaaS**

SMART KEIRI は、従業員10〜50名規模の中小企業を対象とした、シングルテナント型の経費精算・承認ワークフローシステムです。
最新の **Google Gemini 3.0 Flash** を活用した領収書解析（OCR）と、国税庁API連携によるインボイス監査機能を搭載しています。

> ⚠️ **Note**
> 本レポジトリは、**SMART KEIRI の仕様・設計思想・リリースノートを公開するためのドキュメント用レポジトリ**です。
> ソースコード本体は、セキュリティおよび商用ライセンスの都合上、Privateレポジトリにて厳重に管理・運用されています。
>
> 導入のご相談やデモ環境の試用については、[Wantedlyプロフィール](【あなたのWantedly URL】)経由でお問い合わせください。

---

## 🚀 プロダクトの思想 (Philosophy)

### 1. OJI-UX（おじさまUX）
「老眼でも裸眼で読める」を基準とした、徹底的な視認性の追求。
マニュアルを読まなくても使える巨大なボタン配置と、迷わせない画面遷移を実現しています。

### 2. 安心のためのAI
AIを「派手さ」ではなく「ミスの防止」に使用。
Gemini 3.0 Flash が領収書を解析し、インボイス登録番号の実在性を国税庁DBとリアルタイムで照合します。

### 3. 運用ファーストの堅牢設計
安価なマルチテナント型ではなく、顧客ごとに独立した**シングルテナント環境（VPS）**を構築。
開発者自身による日次バックアップと死活監視により、企業の経理データを守ります。

## 📂 System Architecture
堅牢な Django プロジェクト構成を採用し、機能ごとにアプリケーションを疎結合に分割しています。

```text
smart-keiri/
├── config/             # プロジェクト設定・ミドルウェア
├── expenses/           # 経費精算コアロジック (Domain Layer)
│   ├── models/         # 申請・承認・部門管理モデル
│   ├── services/       # Gemini AI解析・国税庁API連携ロジック
│   └── views/          # OJI-UX 実現のためのView層
├── accounts/           # 認証・ユーザー管理
├── templates/          # OJI-UX フロントエンドテンプレート
├── static/             # 静的ファイル (CSS/JS)
├── manage.py
├── requirements.txt
└── .env.example        # 環境変数定義

### 2. 詳細なリリースノート（履歴）を全部載せる
提供いただいた資料にある**「リリースノート（v1.0.0〜v1.1.9）」** [1]〜[2] は、**最強のコンテンツ**です。
「パスワードリセット機能を追加」「Gemini SDKを最新化」「スマホのボタン位置をミリ単位で修正」といった泥臭い改善履歴こそが、**「運用から逃げない」**というあなたの姿勢を雄弁に語ります。

*   **戦略:** `RELEASE.md` という別ファイルを作り、そこに過去の更新履歴を**すべて**コピペして、READMEからリンクを貼ります。
*   **効果:** 更新頻度の高さと内容の具体性が、コードそのものよりも「信頼」に直結します。

### 3. 「実装機能リスト」をチェックボックス形式で羅列する
「何ができるか」を箇条書きにするだけでなく、**GitHubのTask List形式（`[x]`）**で書くと、「開発ロードマップ」のように見えてエンジニア受けが良いです。

**【READMEへの追記案】**
```markdown
## ✅ Implemented Features

### AI & Automation
- [x] **Gemini 3.0 Flash OCR**: 領収書の一括解析・自動入力
- [x] **Smart Tax Splitting**: 軽減税率（8%・10%）の自動按分計算
- [x] **Invoice Validator**: 国税庁APIによる登録番号の実在性チェック
- [x] **Duplicate Detection**: 金額・日付・支払先による重複申請アラート

### Security & Compliance
- [x] **Single Tenant**: 顧客ごとの独立データベース・ストレージ環境
- [x] **Electronic Book Preservation**: 改ざん防止・訂正削除履歴の保存
- [x] **Monthly Closing**: 月次締め（データロック）機能
- [x] **Health Check**: `/health_check` エンドポイントによる死活監視

### OJI-UX (Accessibility)
- [x] **Giant Font Mode**: 老眼対応の文字サイズ・コントラスト調整
- [x] **OJI Toggle Switch**: 標準/拡大表示のワンタップ切替
- [x] **Direct Camera Launch**: モバイルブラウザからのカメラ直接起動

