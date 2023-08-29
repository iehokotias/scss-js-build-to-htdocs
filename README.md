# ビルド環境について

## 特徴
- `webpack`を利用したbuild環境
- `sass`と`js`の書き出しのみのシンプルな設定にしています
- 利用にはpcに `npm` または `yarn` のインストールが必要です

## webpackでのsassの利用

webpackはgulpと比べて多機能で汎用性があります。sassの書き出しだけならgulpで書き出せますがwebpackを採用しています。
webpackには標準でcssやsassを扱う機能がありませんが、`mini-css-extract-plugin`という拡張機能を利用しています。

書き出しは `js`に付随して`css`が書き出される形になるため、`sass`の変更のみの場合でも、`js`をbuildするイメージになります。

## 使い方
現在は`package.json`の`scripts`に以下のようなコマンドリストの記載があります。
```
"scripts": {
  "dev-build": "webpack --mode development",
  "build": "webpack --mode production --node-env=production",
  "dev-build:watch": "webpack --mode development --watch",
  "build:watch": "webpack --mode production --node-env=production --watch",
  "format": "prettier --write 'src/javascript/**/*.js'"
},
```
利用するコマンドは以下のようになります。
```
npm run dev-build
npm run build
npm run dev-build:watch
npm run build:watch
npm run format
```
buildの際はターミナル（コマンドプロント）でこのディレクトリへ移動し、
いずれかのコマンドを実行してみてください。

`npm run build`は公開用のbuildコマンドです。

#### コマンドの説明

- `dev-build` : 非圧縮ファイルを書き出すbuildコマンド
- `build` : 圧縮ファイルを書き出すbuildコマンド
- `dev-build:watch` : `:watch`をつけると変更/保存の度にbuildされます
- `build:watch` : 同上
- `format` : jsのlinterです

# 開発について

- パーツごとにファイルを分割して開発するイメージです。
- scss/jsそれぞれ `./src` 内のファイルの変更を行い、ビルド後のファイルは `./htdocs/dist` 内に書き出されます。
