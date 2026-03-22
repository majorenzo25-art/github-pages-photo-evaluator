# Photo Evaluator

写真評価アプリの GitHub Pages 公開用一式です。

このフォルダには、通常の公開版と、DL 推論 API を使うベータ版が入っています。

## 公開ページ

- 通常公開版: `index.html`
- DL ベータ版: `photo-evaluator-dl-beta.html`

## 主なファイル

- `index.html`
  一般ユーザー向けの通常公開版です。標準評価を行い、条件に応じて ML 補正を使います。
- `photo-evaluator-dl-beta.html`
  DL 推論 API を使うベータ版です。DL が使えない場合は ML、さらに必要なら標準評価へフォールバックします。
- `photo_eval_model.json`
  通常公開版で使うブラウザ側 ML モデルです。
- `photo_eval_public_stats.json`
  通常公開版の公開統計 JSON です。
- `photo-evaluator-pro-delivery-webhook-set.html`
  配送・保存先設定用の補助ページです。
- `manifest.webmanifest`
  PWA 用マニフェストです。
- `service-worker.js`
  キャッシュ制御用の Service Worker です。

## 通常公開版の仕様

- 画像を選択して写真評価
- 総合点と項目別スコア表示
- 履歴表示
- 統計表示
- 感想保存
- 推定カテゴリ表示

## DL ベータ版の仕様

- 画像を選択して DL 評価
- 項目別スコアと総合点を表示
- DL 失敗時は ML フォールバック
- さらに失敗時は標準評価を表示
- 全ユーザー統計とあなたの統計を表示
- DL ベータ専用の評価保存領域を使用

## DL ベータ版の前提

GitHub Pages は静的配信のため、DL ベータ版は外部 API が必要です。

現在の接続先:

- `https://photo-evaluator-dl-api.onrender.com`

主な API:

- `/api/dl/status`
- `/api/dl/predict`
- `/api/dl/evaluation`
- `/api/dl/public-stats`

## 更新時の対象

### 通常公開版を更新する場合

- `index.html`
- 必要に応じて `photo_eval_model.json`
- 必要に応じて `photo_eval_public_stats.json`

### DL ベータ版を更新する場合

- `photo-evaluator-dl-beta.html`

### 通常版と DL 版の両方に関係する場合

- `manifest.webmanifest`
- `service-worker.js`

## デプロイ

このフォルダの内容を GitHub Pages の公開 repo に反映します。

Pages の基本設定:

- Branch: `main`
- Folder: `/ (root)`

## 補足

- DL ベータ版は通常公開版とは分離して使う前提です
- DL 推論は Render 側の API が生きている必要があります
- 統計や評価経路の挙動を変更した場合は、通常版と DL 版の両方で確認してください
