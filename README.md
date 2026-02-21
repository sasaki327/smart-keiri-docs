# SMART KEIRI｜スマート経理　

![Python](https://img.shields.io/badge/Python-3.11%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.x-092E20?style=for-the-badge&logo=django&logoColor=white)
![Gemini](https://img.shields.io/badge/AI-Gemini_3.0_Flash-8E75B2?style=for-the-badge&logo=google&logoColor=white)
![Status](https://img.shields.io/badge/Status-v1.2.0_Released-success?style=for-the-badge)

> **「迷わせず、止まらせず、あとで困らせない」**<br>
> **会計ソフトに渡すデータを完璧にする、中小企業向けAI仕訳・経費管理システム**

> **⚠️ これはデモです。実際のセールスは行っていません。**
> **Note: This repository contains documentation only.**
> 
> 本レポジトリは、**SMART KEIRI** の仕様・設計思想・リリースノートを公開するためのドキュメント用レポジトリです。
> ソースコード本体は、セキュリティおよび商用ライセンスの都合上、Privateレポジトリにて管理されています。


---

## 📖 サービス概要

**SMART KEIRI（スマート経理）** は、従業員10〜50名規模の中小企業に最適化された、**シングルテナント型** の経費精算・承認ワークフローシステムです。

「小さな文字は見落としとミスの原因になる」という実体験に基づき、徹底的な視認性と直感性を追求した **OJI-UX（Optimal Judicious Interface）** を採用。最新の **Google Gemini 3.0 Flash** による領収書解析（OCR）と、国税庁API連携によるインボイス監査を統合し、経理実務の正確性をシステムレベルで担保します。

### コンセプト：プロの仕事を、ストレスフリーに。
大手SaaSのような複雑な設定は不要です。**「経理担当者の負担を最小化し、経営判断を加速させる」** 現場主義の設計により、月末の事務作業を確実に、そして美しく終わらせるための仕組みを提供します。

## 📸 スクリーンショット

### 📱 OJI-UX (Mobile Experience)
「直感的に理解できること」を追求した、独自のインターフェース設計です。

<table>
  <tr>
    <th width="33%">1. Home & Camera</th>
    <th width="33%">2. Standard View</th>
    <th width="33%">3. OJI Mode (👴 Switch On)</th>
  </tr>
  <tr>
    <td align="center"><img src="images/home.png" width="200" alt="Home Screen"></td>
    <td align="center"><img src="images/std.png" width="200" alt="Standard View"></td>
    <td align="center"><img src="images/oji.png" width="200" alt="Giant View"></td>
  </tr>
  <tr>
    <td align="center">迷わず押せる撮影ボタン</td>
    <td align="center">情報密度の高い標準レイアウト</td>
    <td align="center">スイッチONで視認性を極大化</td>
  </tr>
</table>

### 💻 ダッシュボード (PC View)
管理画面は、情報の網羅性と操作スピードを両立させています。
<img src="images/dashboard.png" width="100%" alt="Dashboard PC View">
<img src="images/apply2.png" width="100%" alt="Dashboard PC View">

---

## 🚀 主な機能 (Features)

### ✨ 1. インテリジェント・ドキュメント解析
- **Gemini 3.0 Flash OCR**: 最新のマルチモーダル LLM により、画像から金額・日付・支払先・インボイス番号を高精度に抽出。
- **スマート税率自動判定**: 10%と8%（軽減税率）の混在レシートも自動計算。仕訳の二度手間を解消します。
- **監査ナビゲーション**: AIが読み取り結果の信頼度を評価。確認が必要な箇所を強調表示し、チェック漏れを防ぎます。

### ⚖️ 2. 法制度・コンプライアンス準拠
- **インボイス監査 (国税庁API連携)**:
    - 読み取った登録番号を国税庁DBとリアルタイム照合。事業者名の自動取得と適格性の検証を同時に実行。
- **電子帳簿保存法対応**:
    - 訂正・削除履歴の完全保持（監査ログ）。
    - **月次締めロック機能** により、確定済みデータの改ざんを防止。
- **合計残高試算表 (Trial Balance)**:
    - 経理担当者が使い慣れた「鏡合わせ」のレイアウト。高精度な月次決算を強力にバックアップ。

### 📱 3. 現場特化型 UX
- **OJI-UX Toggle (おじさまスイッチ)**:
    - ワンタップで「標準」と「極大表示」を切り替え。加齢や環境による視認性の障壁を取り払います。
- **Premium Modal (smkConfirm)**:
    - ガラスのような透明感（グラスモーフィズム）を持つ美しい操作ダイアログ。成功・警告・危険などの状態を色彩と同期させ、誤操作を心理レベルで抑制。

### 💎 4. プロフェッショナル・拡張モード（収益管理）
- **オプトイン収益管理**:
    - 通常の経費精算に加え、設定一つで「売上管理」機能を有効化可能。
    - **個人事業主・小規模チーム向け**: 収支を一括管理し、青色申告に必要なデータを自動集計。そのまま会計ソフトへインポート可能です。

---

## 📂 System Architecture

堅牢な Django プロジェクト構成を採用し、ビジネスロジックを独立させた保守性の高い設計です。

```text
smart-keiri/
├── config/             # システム全体の設定・セキュリティ
├── cases/              # 経費精算・承認・仕訳コアロジック
│   ├── models/         # 法令準拠の監査ログを備えたデータ構造
│   ├── services/       # AI解析・行政API連携サービス
│   └── views/          # OJI-UX & 会計統計処理
├── static/             # プレミアムUIリソース (CSS/JS)
└── requirements.txt    # 依存ライブラリ (google-genai, pillow等)
```

## 🛠 技術スタック (Tech Stack)

| Category | Technology |
| :--- | :--- |
| **Backend** | Python 3.11+, Django 5.x |
| **Database** | PostgreSQL, Redis (Cache) |
| **AI Experience** | **Google Gemini 3.0 Flash** (Generative AI) |
| **Public API** | 国税庁 登録事業者公表システム Web-API |
| **Infra** | Linux VPS (Dedicated Environment), Docker |

---

## 📝 Release Notes (History)

### v1.2.0 (2026/02/21)
- **SMK プレミアム・デザイン導入**: ソリッドカラーと精緻なシャドウ、グラスモーフィズムを採用。
- **プロ・モードの洗練**: 収益（売上）管理のオプトイン導入。個人事業主の確定申告までカバー。
- **管理者直接修正**: 承認後データの最終調整機能（完全履歴保持）。
- **インテリジェント重複検知**: AI解析後の重複申請を即座にアラート。

### v1.1.7 (2026/02/14)
- **マルチ会計ソフト連携**: 弥生会計・freee・マネーフォワード形式のCSVエクスポートに対応。

---

## 📬 Contact / お問い合わせ

本システムは、設計から運用保守までを一貫して提供する **「顔の見えるSaaS」** です。
現在はデモ公開中につき、個別のご案内を行っております。
