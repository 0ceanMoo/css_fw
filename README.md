css_fw
====

dddrを参考にすること

BEMのアイデア

```
_Component
--modifier
__utils

ProjectClass      サイト特有のクラス
actionController  サイト特有のJS用クラス
```


最新情報
----
やっぱりコンポネントも自分で作ろう
いくつかCSSフレームワーク試したけど、HTMLの構造が気に食わない
ちょっと違うことしようとすると、途端にできない。

ドキュメント見ながら、ああだこうだしてる時間があるなら、
普通にクラスあててデザイン入れられると思うん。

レイアウトは、CSS3のGridレイアウトで問題ない

* フォームをどうにかしたい
* ボタンもどうにかしたい

薄いCSSフレームワークは試す価値ありかな

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


