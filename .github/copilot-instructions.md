# Copilot instructions — offing-legal

沖凪ろぐの法的文書サイト。**素のHTML**、ビルド・依存なし。詳細は `CLAUDE.md`。

- `index.html` / `terms.html` / `privacy.html` / `style.css` を直接編集する。ビルド工程・npm scripts はない。
- 全コンテンツ日本語（`lang="ja"`）、ミニマル・余白重視。色は offing アプリの `design/tokens.ts` と統一。
- ルーティング・ヘッダは `staticwebapp.config.json`。`main` への push で Azure Static Web Apps へ自動デプロイ。
- 規約文面はドラフト。AIが文面を確定させず、本番反映前に法務レビューを促す。
