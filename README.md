# 勤怠打刻（シフト対応）

シフト勤務に対応した、スマホ用の勤怠打刻Webアプリです。
サーバー不要。GitHub Pages で公開して使います。

## ファイル構成

| ファイル | 役割 |
|---|---|
| index.html | アプリ本体（画面・処理をすべて含む） |
| encoding.min.js | CSVをShift_JISに変換するライブラリ（encoding-japanese / MIT） |
| sw.js | オフラインでも画面を開くためのサービスワーカー |
| manifest.webmanifest | ホーム画面に追加したときの設定 |
| icon-192.png / icon-512.png / apple-touch-icon.png | アイコン |
| encoding-japanese-LICENSE.txt | ライブラリのライセンス |

## 公開手順（GitHub Pages）

1. GitHubで新しいリポジトリを作成（Public）
2. 上記ファイルをすべてリポジトリ直下にアップロード
3. Settings → Pages → Source「Deploy from a branch」、Branch「main」「/(root)」→ Save
4. 表示されたURL（https://ユーザー名.github.io/リポジトリ名/）を配布

## 更新手順

1. 変更したファイルをアップロード
2. `sw.js` の `CACHE` の版番号（例：`'v1.3.2'`）を変更してアップロード
3. `index.html` の `APP_VERSION` も合わせて変更すると、設定画面の表示が更新される

## データの保存先

- 記録は各端末のブラウザ内（localStorage、キー名 `shift-kintai.v1`）に保存
- GitHub やその他のサーバーには送信しない
- 月末にCSV（Shift_JIS、日別1行）を LINE・メールで送付
