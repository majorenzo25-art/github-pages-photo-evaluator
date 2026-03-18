# GitHub Pages Photo Evaluator

このフォルダは公開向け GitHub Pages 用の静的配信セットです。

## 含まれるもの

- `index.html`
- `photo-evaluator-pro-delivery-webhook-set.html`
- `photo_eval_model.json`
- `service-worker.js`
- `manifest.webmanifest`

## 学習モデルについて

公開版は `photo_eval_model.json` を読み込んで補正モデルを使います。  
ただし、モデル件数が `minimum_ml_samples = 30` 未満の間は `Rule-based` にフォールバックします。

## カテゴリ仕様

UI 表示は日本語ですが、保存や送信では次の内部コードを使います。

| UI表示 | 内部コード |
| --- | --- |
| 人物 | `portrait` |
| 風景 | `landscape` |
| 動物 | `animal` |
| 花・植物 | `flora` |
| 食べ物 | `food` |
| その他 | `other` |

複数選択は `|` 区切りです。例: `landscape|animal`

## 注意

- 旧学習データは使いません
- 新仕様で収集したデータだけを学習対象にします
- 学習自体は GitHub Pages 上では行いません
- 学習済み `photo_eval_model.json` を別環境で更新して、このフォルダへ反映します
