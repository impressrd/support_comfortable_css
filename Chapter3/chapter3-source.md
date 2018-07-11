# 気持ちよく書けるCSS


## メディアクエリーでレスポンシブ化

```HTML
<meta name="viewport" content="width=device-width, initial-scale=1">
```

```CSS
.nav {
  display: inline-block;
}
@media screen and (max-width: 980px) and (min-width: 321px) {
  h1 {
    padding: 0.1em;
  }
}
@media screen and (max-width: 320px) {
  .nav {
    display: block;
  }
}
```

```HTML
<div class="global-header">
  <div class="logo">
    株式会社〇〇
  </div>
  <div class="menu">
    <a href="#">会社概要</a> <a href="#">サービス</a>
  </div>
</div>
```

```CSS
.global-header {
  display: flex;
}
.logo {
  /* 広げられるところまで広げる */
  flex: 1; /* flex: 1 1 0; と同等 */
}
.menu {
  flex: initial; /* flex: 0 1 auto;（初期値）と同等のため記述しなくても可 */
}
```

```HTML
<div class="tag-wrapper">
  <div>プロジェクトマネージャー</div>
  <div>サーバーエンジニア</div>
  <div>システムエンジニア</div>
  <div>プログラマー</div>
  <div>フロントエンドエンジニア</div>
  <div>デザイナー</div>
</div>
```

```CSS
.tag-wrapper {
  display: flex;
  flex-wrap: wrap;
}
```

```CSS
.flex-wrapper {
  display: flex;
  flex-direction: row; /* 左から右（初期値） */
  flex-direction: row-reverse; /* 右から左 */
  flex-direction: column; /* 上から下 */
  flex-direction: column-reverse; /* 下から上 */
}
```

```CSS
.flex-wrapper {
  display: flex;
  justify-content: flex-start; /* 左揃え（初期値） */
  justify-content: flex-end; /* 右揃え */
  justify-content: center; /* 中央揃え */
  justify-content: space-between; /* 最初と最後を端に寄せて均等配置 */
  justify-content: space-around; /* 均等配置 */
}
```

```CSS
.flex-wrapper {
  display: flex;
  align-items: stretch;  /* 高さいっぱい（初期値） */
  align-items: flex-start; /* 上揃え */
  align-items: flex-end; /* 下揃え */
  align-items: center; /* 中央揃え */
  align-items: baseline; /* 文字のベースライン揃え */
}
```

```CSS
.flex-wrapper {
  display: flex;
  flex-wrap: wrap;
  align-content: stretch; /* 高さいっぱい（初期値） */
  align-content: flex-start; /* 上揃え */
  align-content: flex-end; /* 下揃え */
  align-content: center; /* 中央揃え */
  align-content: space-between; /* 最初と最後を端に寄せて均等配置 */
  align-content: space-around; /* 均等配置 */
}
```

```CSS
.flex-wrapper {
  display: flex;
}
.flex-child {
  align-self: auto; /* 親要素の align-items の値による（初期値） */
  align-self: flex-start; /* 上寄せ */
  align-self: flex-end; /* 下寄せ */
  align-self: center; /* 中央寄せ */
  align-self: baseline; /* 文字のベースライン揃え */
  align-self: stretch;  /* 高さいっぱい */
}
```

```HTML
<div class="tag-wrapper">
  <div>プロジェクトマネージャー</div>
  <div>サーバーエンジニア</div>
  <div>システムエンジニア</div>
  <div>プログラマー</div>
  <div>フロントエンドエンジニア</div>
  <div>デザイナー</div>
</div>
```

```CSS
.tag-wrapper {
  display: flex;
  flex-wrap: wrap;
}
.tag-wrapper > :last-child {
  order: -1; /* 一番初めに来る */
}
```


## 画像を使わないデザイン

```CSS
.class {
  background-image: linear-gradient(90deg, #fff 0%, #666 100%);
}
```

```CSS
.class {
  background-image: repeating-linear-gradient(#fff 0, #fff 2px, #999 2px, #999 4px);
}
/* もしくは以下 */
.class {
  background-image: linear-gradient(#fff 0, #fff 2px, #999 2px, #999 4px);
  background-size: 1px 4px;
}
```

```CSS
button {
  border-radius: 12px;
}
```

```CSS
img {
  border-radius: 50%;
}
```

```CSS
.class {
  text-shadow: 3px 5px 1px #aaa;
}
```

```CSS
.class {
  box-shadow: 0 2px 10px 1px rgba(0, 0, 0, 0.5);
}
```

```CSS
.balloon {
  background-color: #ccc;
  position: relative;
}
.balloon::before {
  display: block;
  content: '';
  position: absolute;
  bottom: -16px;
  left: 16px;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 16px 12px 0 12px;
  border-color: #ccc transparent transparent transparent;
}
```


## 値の計算

```CSS
.class {
  width: calc(100% - 1px);
  height: calc(100vh - 30px);
}
```


## 色の指定

```CSS
.class {
  /* すべて紫色を表している */
  color: rebeccapurple; /* この色はIE11では指定できませんが…… */
  color: #663399;
  color: #639;
  color: rgb(102, 51, 153);
  color: rgb(40%, 20%, 60%);
  color: rgba(102, 51, 153, 1);
  color: hsl(270, 50%, 40%);
  color: hsla(270, 50%, 40%, 1);
  /* 透明 */
  color: transparent;
}
```

```CSS
.class {
  color: red;
  border: 1px solid currentColor; /* ボーダー色が赤になる */
}
```


## 最初や最後の要素を指定

```CSS
p:last-child {
  margin-bottom: 0;
}
```

```CSS
p:not(:last-child) {
  margin-bottom: 1em;
}
```


## 変形

```CSS
.class {
  transform: rotate(-45deg);
  transform-origin: 0 0; /* 原点を決める */
}
```

```CSS
.image {
  transform:
    perspective(500px) /* ユーザーとの距離が500px離れていると設定 */
    translateX(120px) /* 右に120px移動 */
    translateY(-40px) /* 上に40px移動 */
    translateZ(-100px); /* perspective() で指定した距離からさらに100px遠ざかる */
  transform-origin: 0 0;
}
```

```HTML
<img src="150x150.png" alt="" class="image_1">
<img src="150x150.png" alt="" class="image_2">
<img src="150x150.png" alt="" class="image_3">
```

```CSS
.image_1 {
  transform:
    scaleX(0.5)
    scaleY(1.2);
}
.image_2 {
  transform:
    perspective(500px)
    translateZ(-200px); /* z軸の奥に移動することで伸縮 */
}
.image_3 {
  transform:
    /* この順番で指定 */
    perspective(500px)
    scaleZ(4) /* -200pxを4倍離す指定 */
    translateZ(-200px);
}
```

```HTML
<img src="150x150.png" alt="" class="image_1">
<img src="150x150.png" alt="" class="image_2">
<img src="150x150.png" alt="" class="image_3">
```

```CSS
.image_1 {
  transform:
    rotate(60deg);
}
.image_2 {
  transform:
    rotateX(60deg);
}
.image_3 {
  transform:
    perspective(500px)
    rotateX(60deg);
}
```

```CSS
.image {
  transform: matrix(1, 0, 0, 1, 0, 0);
}
```

```CSS
.image {
  transform: matrix(0.866, 0.5, -0.5, 0.866, 0, 0);
}
```

```CSS
.image {
  transform: matrix(1, 0, -1, 1, 0, 0);
}
```


## 状態の変化にアニメーションを加える

```CSS
button {
  box-shadow: 0 1px 5px rgba(0, 0, 0, 0.2);
}
button:hover {
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
  transition: box-shadow 0.6s linear;
}
```


## 状態にアニメーションを加える

```CSS
@keyframes fadein {
  0% {opacity: 0;}
  100% {opacity: 1;}
}
.class {
  animation: fadein 2.5s;
}
```


## 背景画像の大きさを調整

```CSS
.hero-image {
  width: 100%;
  height: 200px;
  background-image: url(image.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}
```

```CSS
.class {
  width: 600px;
  height: 200px;
  background-image: linear-gradient(
    135deg,
    transparent 0,
    transparent 25%,
    #ccc 25%,
    #ccc 50%,
    transparent 50%,
    transparent 75%,
    #ccc 75%,
    #ccc 100%
  );
  background-size: 8px 8px;
}
```


## カウンター

```CSS
h2 {
  display: list-item;
  list-style-type: decimal; /* 数字を表示させたい…… */
}
```

```HTML
<ol>
  <li>lorem</li>
  <li>lorem</li>
  <li>lorem</li>
</ol>
```

```CSS
ol {
  counter-reset: hoge; /* ol要素が出現するごとに値をリセット */
  list-style-type: none;
}
li::before {
  counter-increment: hoge; /* hoge と命名されたカウンターを増加 */
  content: counter(hoge) ' '; /* hoge と命名されたカウンターを呼び出す */
}
```

```HTML
<ol>
  <li>lorem</li>
  <li>lorem</li>
  <li>lorem
    <ol>
      <li>lorem</li>
      <li>lorem</li>
      <li>lorem</li>
    </ol>
  </li>
</ol>
```

```CSS
ol {
  counter-reset: cnt;
  list-style-type: none;
}
li::before {
  counter-increment: cnt;
  content: '[' counters(cnt, '-', decimal-leading-zero) '] ';
}
```

```HTML
<h1>サイト名</h1>

<h2>H2サブタイトル</h2>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>

<h2>H2サブタイトル</h2>
<h3>H3</h3>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
<h3>H3</h3>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>

<h2>H2サブタイトル</h2>
<h3>H3</h3>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
<h3>H3</h3>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
```

```CSS
h1 {
  counter-reset: sub-title-h2;
}
h2 {
  counter-reset: sub-title-h3;
}
h2::before {
  counter-increment: sub-title-h2;
  content: counter(sub-title-h2) ' ';
}
h3::before {
  counter-increment: sub-title-h3;
  content: counter(sub-title-h2) '-' counter(sub-title-h3) ' ';
}
```


## ボーダーに画像を設定

```CSS
.class {
  border: 30px solid #ededed;
  border-image: url(scroll.svg) 45% fill;
}
```

```CSS
.class {
  border: 30px solid #888;
  background-color: #ddd;
  border-image:
    /* source        slice width outset repeat */
    url(border_img.png) 30 / 30px / 0 space;
}
```

```CSS
.class {
  border: 30px solid #888;
  background-color: #ddd;
  border-image:
    /* source         slice width outset repeat */
    url(border_img.png) 30 / 45px / 6px round;
}
```


## \:target \:checked をトリガー代わりに

```HTML
<div id="top">
  <a href="#hoge">メニュー</a>
</div>
<div id="hoge">
  <a href="#top">x</a>
  <ul>
    <li>メニュー1</li>
    <li>メニュー2</li>
    <li>メニュー3</li>
  </ul>
</div>
```

```CSS
#hoge {
  position: absolute;
  max-width: 300px;
  left: -300px;
  transition: 0.5s;
}
#hoge:target {
  left: 0;
}
```

```HTML
<label for="modal-check">Open</label>
<input type="checkbox" id="modal-check">
<span class="modal">
  <label for="modal-check">Close</label>
</span>
```

```CSS
.modal {
  display: none;
  width: 50vw;
  height: 50vh;
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  margin: auto;
  background-color: #ccc;
  box-shadow: 0 0 0 9999px rgba(0, 0, 0, 0.8);
}
#modal-check {
  display: none; /* 非推奨ですがコード単純化のために用いています */
}
#modal-check:checked + .modal {
  display: block;
}
```


## その他の便利なCSS

```CSS
.class {
  column-count: 3;
}
```

```CSS
.class {
  column-count: auto;
  column-width: 2em;
}
```

```HTML
<a href="http://example.com" style="pointer-events: none;">リンク</a>
```

```CSS
@font-face {
  font-family: 'hogehoge';
  font-style: normal;
  font-weight: 700;
  url(hogehoge.otf) format('opentype');
}
.num {
  font-family: 'hogehoge', sans-serif;
}
```

```CSS
p {
  font-family: 'Hiragino Sans';
  font-feature-settings: 'pkna';
}
```

```CSS
* {
  box-sizing: border-box;
}
```

```CSS
pre {
  background-clip: padding-box; /* 初期値は border-box */
}
```

```CSS
div {
  width: 90px;
  height: 90px;
  background-image:
    url(data:image/png;base64,iVBORw0KGgoAAAA
      （中略）
      apO1ak6VacaS0PRkODjlzsAAAAASUVORK5CYII=
    );
}
```

```CSS
:focus {
  outline: 0; /* デフォルトでも設定されているためリセットしている */
  box-shadow: 0 0 0 2px rgba(19, 177, 241, 0.4);
}
```

## もう使ってもいいだろうというCSS

```CSS
button {
  -moz-appearance: none;
  -webkit-appearance: none;
  appearance: none;
}
```

```HTML
<section>
  <h2>カテゴリー</h2>
  <p>プロジェクトマネージャー</p>
  <p>サーバーエンジニア</p>
  <p>システムエンジニア</p>
  <p>プログラマー</p>
  <p>フロントエンドエンジニア</p>
  <p>デザイナー</p>
</section>
```

```CSS
h2 {
  position: sticky;
  position: -webkit-sticky;
  top: 0;
}
```

```HTML
<div class="wrapper">
  <header>ヘッダー</header>
  <main>
    メイン
  </main>
  <aside>
    サイドメニュー
  </aside>
  <footer>
    フッター
  </footer>
</div>
```

```CSS
.wrapper {
  display: grid;
  grid-template-rows: auto 1fr 80px;
  grid-template-columns: auto 300px;
  height: 100vh;
}
header {
  grid-row: 1;
  grid-column: 1 / span 2;
}
main {
  grid-row: 2;
  grid-column: 1;
}
aside {
  grid-row: 2;
  grid-column: 2;
}
footer {
  grid-row: 3;
  grid-column: 1 / span 2;
}
```

```CSS
@supports (display: grid) {
  .container {
    display: grid;
  }
}
```

```CSS
@supports not (display: grid) {
  .container > * {
    display: float;
  }
}
```

```CSS
@supports (transform-style: preserve) or (-moz-transform-style: preserve) {
  /**/
}
@supports (position: sticky) and (transform-origin: 5% 5%) {
  /**/
}
```
