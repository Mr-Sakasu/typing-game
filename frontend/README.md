# Typing Game Frontend

Typing Game の Vue 3 フロントエンドです。入力判定、タイマー、進捗ゲージ、効果音、ランキング表示を担当し、Rust/Actix Web バックエンドと `axios` で通信します。

## 作成物の説明

プレイヤー名を入力して START を押すと、ランダムに選ばれた単語が出題されます。正しく入力すると次の問題へ進み、全問クリア後にスコアをバックエンドへ送信してランキングを表示します。

## 主な機能

- タイピング問題のランダム出題
- 入力内容と現在の問題文のリアルタイム照合
- クリアタイム計測と `mm:ss:ms` 形式の表示
- 進捗ゲージによるクリア状況の可視化
- 正解、ミスタイプ、入力中の効果音再生
- スコア登録、順位取得、ランキング取得 API との連携

## 技術情報

- Vue.js 3
- JavaScript
- Vue CLI
- axios
- MP3 audio assets

## 環境変数

```bash
VUE_APP_BACKEND_URL=http://localhost:8000
```

## Commands

```bash
npm install
npm run serve
npm run build
npm run lint
```
