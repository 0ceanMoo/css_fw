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
  * pug
  * pug-cli

### ファイルレイアウト
* assets
  * scss：ソース置き場
    * main.scss
    * _xxx.scss
  * pug
    * index.pug
* public
  * index.html
  * css ：成果物を吐き出す

