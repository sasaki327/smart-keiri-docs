# smart-keiri-docs
中小企業の「現場」に特化したAI経費精算SaaS｜Gemini 3.0 Flash搭載 / インボイス・電帳法完全対応 / シングルテナント構成 / Django 5.x &amp; PostgreSQL
して書きます。 以下の構成をコピペして、トップに貼り付けてください。
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
