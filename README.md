css_fw
====

概要
----
自作のCSSフレームワークのユーティリティだけ版

ある程度デザインの入ったパーツやコンポネントやらは大変なので、一般的なFWに任せる
ユーティリティ的なのは、サクッと使いたいので、自前にする

環境作り
----
### 参考
https://iwb.jp/node-sass-autoprefixer-scss-compile/

### ソフトウェア
* yarn
  * node-sass
  * node-sass-import
  * autoprefixer
  * postcss
  * postcss-cli

### ファイルレイアウト
* css ：成果物を吐き出す
* scss：ソース置き場
  * main.scss
  * _xxx.scss

### package.json
```
  "dependencies": {
    "autoprefixer": "^8.6.4",
    "node-sass": "^4.9.0",
    "node-sass-import": "^2.0.1",
    "postcss": "^6.0.23",
    "postcss-cli": "^5.0.1"
  },
  "scripts": {
    "start": "yarn build-css && yarn autoprefixer",
    "build-css": "node-sass --include-path scss scss/main.scss css/util.css --output-style expanded",
    "autoprefixer": "postcss --use autoprefixer --no-map css/util.css -d css/"
  },
  "browserslist": [
    "last 2 versions",
    "not ie < 11",
    "Android >= 4",
    "iOS >= 9"
  ]
```
