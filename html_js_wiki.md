

# html

`span`
インラインタグ

`aside`
余談・補足情報のセクションのタグ

# js


# jQuery
`console.log()`
コンソールに出力する
クロームならデベロッパーツールからconsoleで確認できる

---

`.children()`
現在マッチしている要素の子要素を取得
例
```js
$(.picture_field).children().length;
```
id `.picture_field`の子要素数を取得する
classなども指定できる

---

`$().append()`
html要素を追加する
例
```js
$('div').append('<p><strong>要素の追加テストです。</strong></p>')
```
`div`タグの最後に`append`引数を追加する
idやclassでも指定できる

---
`.remove()`
要素を丸ごと消す

---
`.fadeIn()`
`.fadeOut()`
フェードしながら表示非表示ができる

---

`.each`
HTML要素に対する繰り返し
```HTML
<ul>
  <li>Ruby</li>
  <li>JavaScript</li>
  <li>PHP</li>
</ul>
```
```js
$('li').each(function(index, element){
  console.log(index + ':' + $(element).text());
})
```

配列・オブジェクトに対する繰り返し
```js
var array = ['Rails', 'jQuery', 'FuelPHP'];

$.each(array, function(index, value){
  console.log(index + ':' + value);
})
```
どちらも出力結果は以下のようになる
`0:Ruby
 1:JavaScript
 2:PHP`
