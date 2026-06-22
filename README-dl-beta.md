# Photo Evaluator DL Beta for GitHub Pages

このファイルは、`photo-evaluator-dl-beta.html` を GitHub Pages に反映するときの専用メモです。

## 対象ファイル

- `photo-evaluator-dl-beta.html`

必要に応じて一緒に確認するファイル:

- `manifest.webmanifest`
- `service-worker.js`

## この画面の役割

`photo-evaluator-dl-beta.html` は、DL版の写真評価画面です。

できること:

- 写真を1枚ずつ評価
- DL推論またはMLフォールバックで総合点と項目別点数を表示
- 推定ジャンルを表示
- 点数評価とジャンル評価のフィードバックを保存
- 端末内タイムラインを表示
- 共有保存先へ評価結果を送信

## GitHub Pages に上げるもの

GitHub Pages に上げるのは、基本的に次です。

- `photo-evaluator-dl-beta.html`

共通公開物も更新した場合は次も反映します。

- `manifest.webmanifest`
- `service-worker.js`

## GitHub Pages に上げても動かないもの

この画面は HTML だけでは完結しません。

次の API が別サーバー側に必要です。

- `/api/dl/predict`
- `/api/dl/evaluation`
- `/api/dl/public-stats`
- `/api/admin/status`

つまり:

- 画面本体は GitHub Pages
- DL推論と共有保存は Render またはローカルAPI

です。

## 保存先の切り替え

画面内の `DL保存先` では次を切り替えます。

- `Render API`
- `ローカルAPI (127.0.0.1:8788)`

使い分け:

- 一般公開確認: `Render API`
- 開発者版ハブの `DL評価写真統計` に反映したい場合: `ローカルAPI (127.0.0.1:8788)`

## 共有保存について

DL版では、結果を2系統で扱います。

1. 端末内保存
2. 共有保存

端末内保存:

- ブラウザ内のタイムライン表示用
- API が落ちていても残ることがある

共有保存:

- `/api/dl/evaluation` に送信
- 開発者版ハブの DL統計に反映される対象

## 現在の主な表示要素

- `📸 PHOTO EVAL（β）`
- DL版タイムライン
- 写真評価履歴
- 件数表示
- 全件削除
- 個別削除
- 点数評価
- ジャンル評価

## デプロイ時の確認

1. `photo-evaluator-dl-beta.html` を GitHub Pages 公開リポジトリへ反映する
2. GitHub Pages 公開URLで画面が開くことを確認する
3. `DL保存先` が想定どおりか確認する
4. 画像を選んで評価できることを確認する
5. タイムラインへ端末内保存されることを確認する
6. 共有保存先APIが有効なら、評価結果が共有保存されることを確認する

## 注意

- この画面は現行公開入口 `index.html` とは別です
- `LEGACY_KEEP` 扱いのため、更新時は現行公開版との役割差を意識します
- GitHub Pages 側では学習処理自体は行いません
- 学習済みDLモデルはサーバー側に配置されている必要があります
