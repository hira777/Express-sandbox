# Hello World!

Express アプリケーションを起動して、Hello World!を出力してみる。

以下を`node app.js`を実行し、ブラウザで`localhost:3000`にアクセスすれば、Hello World!が表示されたページが表示される。

**app.js**

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(3000, () => {
  console.log('Example app listening on port 3000!');
});
```

## `express()`

Express モジュールによってエクスポートされる最上位関数であり、Express アプリケーション（`app`オブジェクトとも言われる）を作成する。

`app`オブジェクトは以下のようなメソッドや

- HTTP リクエストのルーティング
- ミドルウェアの設定
- HTML のレンダリング
- テンプレートエンジンの登録

アプリケーションの動作に影響を与える設定（プロパティ）等がある。

また、`app`オブジェクトは

- `request`オブジェクトを`req.app`
- `response`オブジェクトを`res.app`

として参照できる。

## `app.get()`

HTTP GET リクエストに対してのルーティングを定義する。

ルーティングとはクライアントからの要求（GET、POST）にどのように応答するか制御する仕組みであり「URL に応じて実行する処理を指定する」ぐらいの認識で問題ない。

以下はルートパス（'/'）にリクエストがあった際に`res.send()`で HTTP レスポンスを送る（返す）。

```js
app.get('/', (req, res) => {
  res.send('Hello World!');
});
```

## `app.listen()`

UNIX ソケット（サーバー）を起動し、指定されたホストとポートの接続を待機する。

Node.js の [`http.Server.listen()`](https://nodejs.org/api/http.html#http_server_listen) と同じ。

以下はポート 3000 の接続に対して、コールバックを実行する。

```js
app.listen(3000, () => {
  console.log('Example app listening on port 3000!');
});
```
