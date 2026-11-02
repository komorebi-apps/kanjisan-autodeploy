# 幹事さん — 自動導入試験版 v0.2

元アプリ: MicroCoordinator v0.7.23-dev（統合カレンダー）

> **試験用です。** まだCloudflare実機での自動導入確認は完了していません。実データを登録しないでください。

## 自動導入（試験）

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/komorebi-apps/kanjisan-autodeploy)

このボタンは **公開リポジトリへのファイル登録後** に使用できます。

1. CloudflareとGitHubのアカウントでログインします。
2. 導入画面で **新しい** Worker名・D1データベース名を指定します。既存のWorkerやD1を選ばないでください。
3. `ADMIN_TOKEN` に32文字以上の安全なランダム文字列を設定します。**公開GitHubやスクリーンショットに表示しないでください。**
4. 作成・公開を実行し、WorkerのURLで幹事さんを開きます。
5. アプリの管理者ログインに、設定した `ADMIN_TOKEN` を入力します。

## 内容

- `worker.js` — v0.7.23-dev の元コードを無変更で収録
- `wrangler.json` — WorkerとD1の自動作成用設定。`database_id` は仮IDで、導入時にCloudflareが実IDへ差し替える想定です
- `package.json` — Cloudflare用デプロイ設定、秘密文字列の入力案内
- `.dev.vars.example` — ローカル試験用の例（**本当の秘密文字列は書かない**）
- `.gitignore` — 秘密ファイル等の誤登録防止

## 留意事項

- 元アプリはD1のテーブルを利用時に `CREATE TABLE IF NOT EXISTS` で作成するため、今回は別途のSQL移行処理を追加していません。
- **このZIPそのものではなく、展開したファイル**をGitHubのリポジトリ直下に登録してください。
- `.dev.vars`、`.env`、実際のパスワード、データバックアップは絶対に公開しないでください。
- Cloudflareの自動導入の実際の画面、秘密文字列の設定、D1の自動作成、管理者ログインは未検証です。
- 公開GitHub上のソースコードは誰でも読めます。運用前に認証・参加者リンク等の安全性の別途確認が必要です。

公式資料: https://developers.cloudflare.com/workers/platform/deploy-buttons/
