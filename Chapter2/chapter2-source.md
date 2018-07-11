# CSSの指定の基本

## 単位

```CSS
html {
  font-size: 62.5%; /* 10px */
}
h1 {
  font-size: 2.4rem; /* 24px（1rem = 10px にしたため） */
}
```

## 擬似クラス

```CSS
a:link {
  color: #13b1f1;
}
a:visited {
  color: #017bad;
}
a:hover {
  color: #80daff;
  text-decoration: none;
}
a:active {
  color: #13b1f1;
}
```

```HTML
<input class="num" name="num" type="number" min="1" max="10" value="">
```

```CSS
.num:out-of-range {
  background-color: rgba(255, 0, 0, 0.1);
}
```

```CSS
li:nth-child(3n+1) {
  background-color: #ccc;
}
```

```CSS
p:first-of-type {
  background-color: #ccc;
}
```

```HTML
<div>
  <div>ここは変わらない</div>
  <p>ここの背景色が変わる</p>
  <p>ここは変わらない</p>
  <div>
    <p>ここの背景色が変わる</p>
    <p>ここは変わらない</p>
  </div>
</div>
```

```HTML
<a href="#section2">見出し2</a>
<div id="section2">...</div>
```

```CSS
div:target {
  background-color: #ccc;
}
```

## 擬似要素

```CSS
.class::before {
  content: '“';
}
.class::after {
  content: '”';
}
```