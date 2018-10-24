css_fw
====

dddrを参考にすること

レイアウト
https://parashuto.com/rriver/development/block-grid-multi-column-layouts-with-nth-child

既存のフレームワークを使わない理由
----
* 命名規則が気に食わない
* タグの構造をいじるのが気に食わない
* ルール覚えるのが面倒
* CSS3のGridレイアウトでも十分（フレームワークの価値って、カラムレイアウトにあると思う
* できる事しかできない。違うことやろうとすると難しい。やり方が違うのか、そもそも出来ないのか、分からない

ドキュメント見ながら、ああだこうだしてる時間があるなら、
普通にクラスあててデザイン入れられると思うん。


自作フレームワークを作る理由
----
本当は、もう疲れたから作りたくない
けど、世にあるフレームワークを使うのはもっと疲れる

ユーティリティだけを面倒みてくれる、薄いCSSフレームワークなら良いかなという理由
っで、結局ボタンやテーブル、フォームなんかも整えて欲しいって感じになったから
コンポネントとして、作ることにした

３大原則
----
Flowによるレイヤリング
  Founcation（reset.cssやnormalize.css
  Layout
  Object
    抽象的コンポネント
    具体的コンポネント
  Utility


マルチクラスでユーティリティ
  class="__mt-10px __fs-12rem __bold __red"

BEMによるコンポネント設計
  Blockがコンポネント、名前空間みたいなもの
  Elementsはコンポネントを構成する要素
  Modifyが見た目のバリエーション

  x class="logo logo-small"
  o class="Logo __small"

仕様
----
Founcation層は、reset.cssやnormalize.cssを使う
レイアウト層は、CSS3のGridレイアウトを使って、サイト・プロジェクトごとに最適なのを作る
オブジェクト層の抽象的なコンポネントは、フレームワークの機能として実装しておく
オブジェクト層の具体的なコンポネントは、サイト・プロジェクトごとに作成する
ユーティリティ層は、自作で作るし、これこそがキモ

サイズは、xs, sm, md, lg, xl のように5段階とする
上下左右は、t,b,l,r
縦方法はy、横方向はxで表す


### 命名
コンポネントは、アンダースコア大文字始まり
ユーティリティは、アンダースコアx2小文字始まり

```
_Component
--modifier
__utils

ProjectClass      サイト特有コンポネント
actionController  サイト特有のJS用クラス
```

### 例
上に大きいmarginが欲しいときは、__mt-xl
上下にpaddingが欲しいときは、__py-md



TODO
----
* Table
  * ボーダー
  * ストレイプ
  * ホバー
  * レスポンシブ
* メニュー
  * 水平
  * タブ
  * 階層
* フォーム
* ボタン

FUTURE
----
* stylus化する？？？
* webpackの導入をどうするか？


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

### tmux
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


### media query
```
_breakpoint.scss 
$breakpoints-up: (
  'xs': 'screen and (min-width: 330px)',
  'sm': 'screen and (min-width: 660px)',
  'md': 'screen and (min-width: 990px)',
  'lg': 'screen and (min-width: 1320px)',
  'xl': 'screen and (min-width: 1650px)',
) !default;
$breakpoints-down: (
  'xs': 'screen and (max-width: 329px)',
  'sm': 'screen and (max-width: 659px)',
  'md': 'screen and (max-width: 989px)',
  'lg': 'screen and (max-width: 1319px)',
  'xl': 'screen and (max-width: 1649px)',
) !default;

@mixin mq-up($breakpoint: md) {
  @media #{map-get($breakpoints-up, $breakpoint)} {
    @content;
  }
}
@mixin mq-down($breakpoint: md) {
  @media #{map-get($breakpoints-down, $breakpoint)} {
    @content;
  }
}

// 使う方
.someClass
  width: 1600px
  @include mq-down(xl)
    width: 1320px
  @include mq-down(lg)
    width: 990px
  @include mq-down(md)
    width: 660px
  @include mq-down(sm)
    width: 320px
```


