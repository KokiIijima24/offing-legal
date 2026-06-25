# offing-legal — AI向け案内

沖凪ろぐ（OFFING / おきなぎログ）の法的文書サイト。**素のHTML**、ビルドツール・依存なし。

## 構成
- `index.html`（ハブ）/ `terms.html`（利用規約）/ `privacy.html`（プライバシーポリシー）/ `style.css`（共有）
- `staticwebapp.config.json` — ルート書換 `/terms→/terms.html` `/privacy→/privacy.html`、セキュリティヘッダ、404→index
- `.github/workflows/azure-static-web-apps.yml` — `main` への push / PR でデプロイ（`skip_app_build: true`、ルート直配信）

## デプロイ
- Azure Static Web Apps（Free / East Asia）。Live: https://witty-pond-00664bc00.7.azurestaticapps.net/
- トークンは GitHub secret `AZURE_STATIC_WEB_APPS_API_TOKEN`。`main` に push すれば自動デプロイ。
- ビルド工程なし。HTMLを直接編集する。npm scripts は無い。

## 規約
- 全コンテンツ日本語（`lang="ja"`）。デザインはミニマル・余白重視。色は offing アプリの `design/tokens.ts` と統一。
- フォントはシステムスタック（Hiragino Sans / Noto Sans JP）。
- ⚠️ 現状の規約文面は **ドラフト**。本番反映前に法務レビューを推奨（AIが文面を確定させない）。
