# Hugo + Vue.js + Laravel mix

Hugo + Vue.js のプロジェクトテンプレート

## 準備
hugo コマンドは使える前提

## 新規作成
表示確認まで。
```bash
git clone https://github.com/kawax/hugo-vue-mix.git my-site
cd ./my-site
yarn install
npm run prod
hugo server
```

http://localhost:1313/

## フォルダ構成

基本的には hugo デフォルトのまま。

### resources
Laravel の `resources` から assets 部分だけ。

### themes/sample
Vue コンポーネントを表示してるだけのサンプルテーマ。
他のテーマを使うには `themes/sample/layouts/_default/baseof.html` を参考に Vue に必要な箇所を追加する。

```html
<link href="/css/app.css" rel="stylesheet">
```

```html
<div id="app">
    
</div>
```

```html
<script src="/js/app.js"></script>
```

### static
`npm run prod` でビルドされたファイルはここに。デプロイ時に `hugo` だけで済むようにビルド済ファイルもgitリポジトリに含める。

## webpack.mix.js
ファイルの出力先を `static` に変更している。`mix()` ヘルパーが使えないので `version()` は使えない。

## 開発時
`npm run server` で起動しつつ `npm run dev` でビルドする。`npm run watch` も一応使えるはず。

## デプロイ前
`npm run prod` でビルドしてコミット。

## デモ
https://hugo-vue-mix.netlify.com/

## Vue コンポーネント

### filter-search
絞り込み検索。とりあえず動くように作っただけなので実際に使う場合は `resources/assets/js/components/Search.vue` を元に書き換える。データソースは `resources/data/posts.json` サーバーがあるならAPIで取得するデータをjsonで直接置いている。

