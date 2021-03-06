# 概要
Laravel-Passportを使っていろいろしたみる。

- Laravel Framework 6.6.1
- PHP 7.3.12
- sqlite

# お試し

このリポジトリ([クライアントアプリ(Laravel\-passportでログインさせる側)](https://github.com/tobibako45/laravel-socialite-practice))とセットでお試し

あとからまとめます。

### Laravelでcloneしたらやること

SqliteでやったのでこちらをCODEBASE2期生の[@avocadoneko](https://twitter.com/avocadoneko)さんのこちらを参考

[【初心者向け】Laravel プロジェクトを clone してブラウザ表示するまで \- Qiita](https://qiita.com/avocadoneko/items/04d3c297064ba6e55a33)

こちらも
```
npm install
npm run dev
```

<br>

#### １、localhost:8080で立ち上げる
```
php artisan serve --port=8080
```

<br>

#### ２、ユーザー作成
http://localhost:8080/registerで、ユーザーを作成。

<br>

#### ３、クライアントアプリを登録
OAuth Clientsの「Create New Client」ボタンでクライアントを登録。

「Name」は自由に。「Redirect URL」を
```
http://localhost:8000/login/passport/callback
```
にする。

<br>

#### ４、クライアントアプリ側の.envファイルに、登録した情報を記入
「Client ID」と「Secret」、リダイレクトURIを、[クライアントアプリ(Laravel\-passportでログインさせる側)](https://github.com/tobibako45/laravel-socialite-practice)の「.env」に記入。
```
PASSPORT_ID=<登録したクライアントID>
PASSPORT_SECRET=＜登録したクライアントsecret＞
PASSPORT_REDIRECT_URI=http://localhost:8000/login/passport/callback
```

<br>

#### ５、クライアントアプリ側を立ち上げてログイン
[クライアントアプリ(Laravel\-passportでログインさせる側)](https://github.com/tobibako45/laravel-socialite-practice)を、
```
php artisan serve
```
で立ち上げる。

```
http://localhost:8000
```
にアクセスして、「Laravel-Passportでログインする」からログイン。
