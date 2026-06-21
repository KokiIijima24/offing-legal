# offing-legal

おきなぎログ（OFFING）の法的文書（利用規約・プライバシーポリシー）を配信する静的サイト。

## 公開URL（本番）

Azure Static Web Apps のデフォルトドメインで配信中。

| ページ | URL |
| --- | --- |
| トップ | https://witty-pond-00664bc00.7.azurestaticapps.net/ |
| 利用規約 | https://witty-pond-00664bc00.7.azurestaticapps.net/terms |
| プライバシーポリシー | https://witty-pond-00664bc00.7.azurestaticapps.net/privacy |

アプリ（offing）側では `app/(tabs)/settings.tsx` の `TERMS_URL` / `PRIVACY_URL` 定数が
この URL を参照する。URL を変えたら両定数も更新すること。

## 構成

- `index.html` — 法的情報トップ（各文書への導線）
- `terms.html` — 利用規約（`/terms` でもアクセス可）
- `privacy.html` — プライバシーポリシー（`/privacy` でもアクセス可）
- `style.css` — 共通スタイル（アプリのデザイントークンと色味を統一）
- `staticwebapp.config.json` — Azure Static Web Apps のルーティング／ヘッダ設定
  （`/terms`・`/privacy` の短縮ルートはここの rewrite で実現）
- `.github/workflows/azure-static-web-apps.yml` — `main` への push で自動デプロイ

## デプロイ

Azure Static Web Apps（本番環境のみ）。`main` ブランチへの push で GitHub Actions が
リポジトリ直下をそのまま配信する（ビルド不要：`skip_app_build: true`）。

### Azure リソース

| 項目 | 値 |
| --- | --- |
| テナント | `04d85cbf-fc37-449b-a3c9-6edc7e8d213b`（koki.iijima.24@gmail.com） |
| サブスクリプション | `003349fe-fe7a-4670-b4f9-34ce665c8187`（Azure subscription 1） |
| リソースグループ | `jca-prod-rg` |
| リソース名 | `offing-legal`（Static Web App、SKU: Free、リージョン: East Asia） |
| デフォルトドメイン | `witty-pond-00664bc00.7.azurestaticapps.net` |

### デプロイトークン

GitHub リポジトリのシークレット `AZURE_STATIC_WEB_APPS_API_TOKEN` に設定済み。
ローテーション・再設定する場合は、新テナントへログインしてトークンを取り直す：

```bash
az login --tenant 04d85cbf-fc37-449b-a3c9-6edc7e8d213b
az staticwebapp secrets list \
  --name offing-legal --resource-group jca-prod-rg \
  --query "properties.apiKey" -o tsv \
  | gh secret set AZURE_STATIC_WEB_APPS_API_TOKEN --repo KokiIijima24/offing-legal
```

> 注: `az` はスポンサープラン（テナント `1c62eaac…`）にも繋がるため、SWA を操作する前に
> 必ず上記 `--tenant` で本番テナントにログイン中であることを確認すること。

## カスタムドメイン（将来）

`offing.ai` 等の独自ドメインに移行する場合は、SWA にカスタムドメインを追加し DNS
（CNAME/TXT）を設定したうえで、上記の公開URL とアプリ側の URL 定数を差し替える。

## 注意

本文書は一般的なテンプレートに基づくドラフトであり、公開・運用にあたっては法務確認を
推奨します。最終更新日は各 HTML の冒頭に記載。
