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

## 🛡️ SMART KEIRI の設計思想と特長

大手SaaSにはない、独自の「安心」と「実利」を追求しています。

### 1. 「専用環境」による圧倒的な安心感
共有サーバー（マルチテナント）ではなく、貴社専用の物理的に独立したサーバー環境を構築します。機密性の高い経理データを他社と混在させることなく、安全に管理。独自のカスタマイズも柔軟に対応可能です。

### 2. 「今の会計ソフト」を変えずに、入力だけを劇的に楽に 
freee、マネーフォワード、弥生会計など、主要な会計ソフトへの連携機能を標準装備。会計ソフトそのものを乗り換える必要はありません。もっとも手間のかかる「現場の入力」と「証憑管理」だけを SMART KEIRI で効率化し、その結果を今のソフトに流し込む。これが最も低リスクで高効率なDXです。

### 3. 「顔の見える」伴走型サポート
導入時の専用サーバー構築から、勘定科目のカスタマイズ、管理者向けのレクチャーまで、システムを提供して終わりではなく、貴社の経理業務が正常に回るまで一貫してサポートします。

---

## 🚀 主な機能 (Features)

### ✨ 1. インテリジェント・ドキュメント解析
- **Gemini 3.0 Flash OCR**: 最新のマルチモーダル LLM により、画像から金額・日付・支払先・インボイス番号を高精度に抽出。
- **「売上モード」専用プロンプト**: 単なるOCRではなく、収入と支出を論理的に判別。実務に基づいた精度の高いカテゴリー提案を行います。
- **監査ナビゲーション**: AIが読み取り結果の信頼度を評価。確認が必要な箇所を優先的にチェックできます。

### ⚖️ 2. インボイス・電帳法への完全対応
- **国税庁API連携**: 領収書の登録番号をリアルタイムで照合。適格請求書発行事業者の有効性をシステムが自動担保。
- **改ざん防止とログ保存**: 電子帳簿保存法が求める「訂正・削除履歴の保持」と「月次締めロック」を完備。

### 📱 3. 現場を迷わせない OJI-UX
- **おじさまスイッチ (OJI Toggle)**: ITに詳しくない現場スタッフでも迷わず使える「極大表示モード」を搭載。視覚的な障壁を取り払い、心理的ハードルを下げます。
- **Premium Design (Glassmorphism)**: 誤操作を抑制する色彩設計と、直感的に「次に何をすべきか」がわかる高品位なインターフェース。

---

## 📂 System Architecture

堅牢な Django プロジェクト構成を採用し、シングルテナント（専用環境）による高い秘匿性と拡張性を確保しています。

```text
smart-keiri/
├── config/             # システム全体の設定・セキュリティ
├── cases/              # 経費精算・承認・仕訳コアロジック
├── static/             # プレミアムUIリソース (CSS/JS)
└── infrastructure/     # 専用VPS/Docker構築スクリプト
```

## 🛠 技術スタック (Tech Stack)

| Category | Technology |
| :--- | :--- |
| **Backend** | Python 3.11+, Django 5.x |
| **Experience** | **Google Gemini 3.0 Flash** (Generative AI) |
| **Public API** | 国税庁 登録事業者公表システム Web-API |
| **Infra** | Linux VPS (Dedicated Environment), Docker |

---

## 📝 Release Notes (History)

### v1.2.0 (2026/02/22)
- **SMK プレミアム・デザイン導入**: ソリッドカラーと精緻なシャドウ、グラスモーフィズムを採用。
- **AI解析の最適化（売上管理対応）**: 収入モードにおいて、正確な顧客名抽出と収益系カテゴリーの優先提案を実現。
- **管理者ワークフローの改善**: 管理者による他部署案件の修正・削除（承認者の保持対応および権限調整）をサポート。
- **システム安定性の向上**: CSV出力のエラー（特殊文字・エンコーディング）対策、一括解析バグの修正。

### v1.1.7 (2026/02/14)
- **マルチ会計ソフト連携**: 弥生会計・freee・マネーフォワード形式のCSVエクスポートに対応。

---

## 📬 Contact / お問い合わせ

本システムは、設計から運用保守までを一貫して提供する **「伴走型SaaS」** です。
現在はデモ公開中につき、セールスは行っていません。
