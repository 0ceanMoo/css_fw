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
    * ＿xxx.scss
  * pug
    * index.pug
* public
  * index.html
  * css ：成果物を吐き出す

### Tmux
上３つ
  * README用
  * pug用
  * scss用
下２つ
  * git用
  * yarn watch


### 脱bootstrap
https://www.flexboxpatterns.com/

色んなフレームワーク見たけど
フレームワークだけでは、部分的に足りないとこが出てくる
結局細かい所は自分で書かないとダメ

ある程度カバーしてくれるだけでいいんだけど、これだったら基礎だけやってもらって
後は差し替えってのが楽になってくる。

レイアウトは、Gridレイアウトがあるから、CSSで大丈夫だ
ボタンやフォームは、フレームワークに面倒見てもらいたい
コンポネントもフレームワークに面倒見てもらいたい

っが、全てを満たすフレームワークがないので、結局自分で書く。
統一感がなくなる。

無限ループだ。


