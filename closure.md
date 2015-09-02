##はじめてのクロージャ

<p style="font-size: 20px;">
    2015/09/02 もとき
</p>

---

###今日のキーワード

- クロージャ

---

###クロージャとは？

<blockquote style="font-size: 25px; text-align: left; margin-left: 0;">
    引数以外の変数を実行時の環境ではなく、自身が定義された環境（静的スコープ）において解決することを特徴とする。関数とそれを評価する環境のペアであるともいえる。
    ...wikipediaより引用
</blockquote>

---

###？？？

---

###つくってみよう

よくわからないので、とりあえず作ってみましょう。

---

###つくってみよう

数字をカウントアップする関数を作ってみます。

```
var num = 0;
function countup(){
    return ++num;
}
```

できた。動かしてみます。

```
console.log( countup() );  // => 1
console.log( countup() );  // => 2

num = 0; // ←

console.log( countup() );  // => 1
```

あれれ。

<!-- カウントアップする関数なのに、途中で0に戻ってしまいました。 -->

---

###つくってみよう

変数を周りから操作できないようにしよう。

```
// var num = 0;
function countup(){
    var num = 0; // ← 移動
    return ++num;
}
```

```
console.log( countup() );  // => 1
console.log( countup() );  // => 1
console.log( countup() );  // => 1
```

できない。（そりゃそうだ）


---

###つくってみよう

そこでクロージャ。

```
var countup = (function(){
    var num = 0;
    return function(){
        return ++num;
    }
})();
```

```
console.log( countup() );  // => 1
console.log( countup() );  // => 2
num = 0;
console.log( countup() );  // => 3
```

おっ




---

---

###参考

<p style="text-align: left;">
    https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AD%E3%83%BC%E3%82%B8%E3%83%A3
    http://d.hatena.ne.jp/keyword/%A5%AF%A5%ED%A1%BC%A5%B8%A5%E3
    https://developer.mozilla.org/ja/docs/Web/JavaScript/Closures
    http://dqn.sakusakutto.jp/2009/01/javascript_5.html
    http://qiita.com/takeharu/items/4975031faf6f7baf077a
    http://satoshi.blogs.com/life/2007/12/javascript-2.html
    http://uhyohyo.net/javascript/9_5.html
</p>



