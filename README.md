# offing-legal

おきなぎログ（OFFING）の法的文書（利用規約・プライバシーポリシー）を配信する静的サイト。

## 構成

- `index.html` — 法的情報トップ（各文書への導線）
- `terms.html` — 利用規約（`/terms` でもアクセス可）
- `privacy.html` — プライバシーポリシー（`/privacy` でもアクセス可）
- `style.css` — 共通スタイル（アプリのデザイントークンと色味を統一）
- `staticwebapp.config.json` — Azure Static Web Apps のルーティング／ヘッダ設定
- `.github/workflows/azure-static-web-apps.yml` — `main` への push で自動デプロイ

## デプロイ

Azure Static Web Apps（本番環境のみ）。`main` ブランチへの push で GitHub Actions が
リポジトリ直下をそのまま配信する（ビルド不要）。

シークレット `AZURE_STATIC_WEB_APPS_API_TOKEN` にデプロイトークンを設定すること。

## 注意

本文書は一般的なテンプレートに基づくドラフトであり、公開・運用にあたっては法務確認を
推奨します。最終更新日は各 HTML の冒頭に記載。
