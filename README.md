# GitHub Pages Deploy Set

このフォルダをそのままGitHubリポジトリに入れると、GitHub Pagesで公開しやすい構成です。

## 含まれるファイル

- `index.html`
  - 公開時の入口ページ
- `photo-evaluator-pro-delivery-webhook-set.html`
  - 正式な起動対象の元ファイル名版
- `manifest.webmanifest`
- `service-worker.js`
- `.nojekyll`

## 公開手順

1. GitHubに新しいリポジトリを作る
2. このフォルダの中身をリポジトリ直下へアップロードする
3. GitHub Pages を `Deploy from a branch` / `main` / `/root` で有効化する
4. 発行された `https://...github.io/.../` を開く

## iPhoneで使う場合

1. SafariでGitHub PagesのURLを開く
2. `起動モード: Hosted Web App (iPhone対応)` を確認する
3. 必要なら「ホーム画面に追加」する

## 補足

- Webhook URLはHTMLに初期設定済みです
- `file://` 直開きではなく、必ずGitHub PagesのHTTPS URLから開いてください
