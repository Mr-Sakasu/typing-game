# Typing Game

Vue 3 のフロントエンドと Rust/Actix Web のバックエンドで作成した、ランキング機能付きのタイピングゲームです。プレイ時間を PostgreSQL に保存し、上位ランキングと自分の順位を確認できます。

- GitHub: https://github.com/Mr-Sakasu/typing-game
- 公開URL: https://typinggame-ufh6.onrender.com/
- 種別: フルスタック Web アプリ、タイピングゲーム、ランキングシステム

<p align="center">
  <img src="https://github.com/Sakasu-TUAT/typing-game/assets/113872797/7b0ab8d8-8cce-4c79-8ec4-c2cfc87ed59a" width="350" height="auto">
</p>

## 作成物の説明

ランダムに出題される単語を入力してクリアタイムを競う Web アプリです。フロントエンドでは入力判定、タイマー、進捗ゲージ、効果音、ランキング表示を実装し、バックエンドではスコア保存、順位計算、ランキング取得 API を提供しています。

## 担当した役割

- Vue 3 によるゲーム画面、入力判定、タイマー、進捗ゲージ、効果音の実装
- `axios` を使ったバックエンド API 連携を実装
- Rust/Actix Web による REST API と CORS 設定を実装
- PostgreSQL と `sqlx` を使ったスコア保存、順位計算、ランキング取得を実装
- Render.com 上でフロントエンド、バックエンド、PostgreSQL を連携する構成を整備

## 直面した課題と解決方法

- フロントエンドとバックエンドを別オリジンで動かすため、環境変数 `FRONTEND_URL` を使って CORS の許可元を切り替えられるようにしました。
- プレイ終了直後にランキングと自分の順位を表示する必要があったため、スコア登録、順位取得、ランキング取得を API として分離しました。
- ゲーム体験が単調になりやすいため、正解、ミスタイプ、入力中の効果音と進捗ゲージを追加し、入力状況がすぐ分かる UI にしました。
- デプロイ環境ごとに URL が変わるため、フロントエンドでは `VUE_APP_BACKEND_URL`、バックエンドでは `RENDER_POSTGRES_INTERNAL_DBURL` と `PORT` を使う構成にしました。

## 技術情報

- Frontend
  - JavaScript
  - Vue.js 3
  - Vue CLI
  - axios
  - audio assets
- Backend
  - Rust
  - Actix Web
  - actix-cors
  - serde / serde_json
  - sqlx
  - PostgreSQL
- Deployment
  - Render.com

## API

- `POST /users`: ユーザー名、スコア、作成日時を保存
- `GET /score_rank/{score}`: 指定スコアの順位を取得
- `GET /ranking/{rank_num}`: 上位ランキングを取得
- `POST /create`: `users` テーブルを作成
- `POST /delete`: `users` テーブルを削除

## 環境変数

### Frontend

```bash
VUE_APP_BACKEND_URL=http://localhost:8000
```

### Backend

```bash
RENDER_POSTGRES_INTERNAL_DBURL=postgres://...
FRONTEND_URL=http://localhost:8080
PORT=8000
```

## Commands

Frontend:

```bash
cd frontend
npm install
npm run serve
npm run build
```

Backend:

```bash
cd backend
cargo run
```

## 関連リポジトリ

- Portfolio: https://github.com/Mr-Sakasu/portfolio
- 競技プログラミング: https://github.com/Mr-Sakasu/abc
- Virtual Contest Bot: https://github.com/Mr-Sakasu/virtual-contest-bot
