---
title: "🔰 Strictモード('use strict')"
---
# `use strict`を書く理由を理解しておこう！
![](https://storage.googleapis.com/zenn-user-upload/6a2add633a7801c2d07aa059.png =400x)

## はじめに
kintoneでJavaScriptカスタマイズをする際に、一番最初の行に書くことの多い`use strict`。
皆さんはどのくらい意識してこの1行を書いていますか。

## そもそも、Strictモード(厳格モード)とは？
まず、 `strict` という単語に注目してみましょう。
この単語は、「厳しい、厳格な、精密な、完全な」という意味を持つ形容詞です。

つまり`use strict`は、「厳格なチェックを行うモードを使用する」という意味です。
さらに詳しくドキュメントを見てみましょう。

> Strictモードを使用すると、通常のJavaScriptの意味にいくつかの変更を加えます。エラーではないが落とし穴になる一部の事柄を、エラーが発生するように変更することで除去します。
>1. JavaScriptエンジンによる最適化処理を困難にする誤りを修正します。
>2. Strictモードのコードは、非Strict モードのコードより高速に実行できる可能性があります。
>3. 将来のECMAScriptで定義される予定の構文の使用を禁止します。
>
>[MDN Web Docs > Strict モード](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Strict_mode)

以上のことから、`use strict` は事前にコードをチェックし、ミスを防ぐことに役立つ1行であることが分かりました。さらに、どの様なコードをチェックしているのか確認したい方は、以下で紹介する「特徴」の内容を読んでみてください。

## 具体例
Strictモードを **①利用しなかった場合**と、
**②利用した場合**にどのような違いがあるのか確認してみましょう。

### ①`'use strict'` を利用していない場合
![](https://storage.googleapis.com/zenn-user-upload/8616a43f7c2d3ef28cebf44a.png =400x)

変数宣言(let, const, var)をしていない `text_a` は、グローバル変数として処理され`console.log(text_a);`が実行されます。

コードが実行されたため、問題なく動作している……と思ったら少し注意してみてください。
実は、JavaScriptはグローバル変数定義を推奨していません。
もし意図せず誤って変数宣言が抜けてしまった場合、グローバル変数として実行されてしまうと他のコードにも影響を及ぼす可能性が高くなってしまいます。

※「なぜグローバル変数がいけないの？と」思った方は [グローバル変数を乱用しない](https://kenju.gitbooks.io/js_step-up-to-intermediate/content/content/part01/avoid_abusing_global_variables.html) や『🔰 変数』Chapterを一読してみてください。

### ②`'use strict'` を利用した場合
![](https://storage.googleapis.com/zenn-user-upload/dbda84b8378ce0a20f41aaf2.png =400x)

`ReferenceError: text_b is not defined`
参照エラー: text_bが変数定義されていないため、エラーが返ります。

`let`を利用して、変数を定義してから実行してみましょう。
![](https://storage.googleapis.com/zenn-user-upload/b80dfa2b7399ab3dc5576595.png =400x)
正しく実行することができました。

このように`'use strict'`を利用すると開発途中で、
エラーになる一部を教えてくれるため、コードを素早く修正できます。

## Strictモードのスコープ
次は、Strictモードのスコープを紹介します。
スコープ(scope)は、「範囲、視野、余地」といった意味を持つ単語です。
つまり、ここではStrictモードを適用する範囲をみていきます。

Strictモードは、**スクリプト全体に適用するか、一部に適用するか**範囲を変えることができます。では、適用方法を確認していきましょう。

```js:全体にStrictモード
((){
  'use strict';
  let text = "こんにちは！Strictモードのスクリプト！";
})();
```

```js:関数のみStrictモード
((){
  function strict() {
    'use strict';
    return "こんにちは！ Strict モードの関数です！";
  }
})();
```

`function`の中に`'use strict';`が定義されています。
つまり、

```js:Strictモードの関数と、非Strictモードの関数
((){
  function strict() {
    'use strict';
    return "こんにちは！ Strict モードの関数です！";
  }

  function non_strict() {
    return "こちらは、Strictモードではありません！";
  }
})();
```

Strictモードの関数と、非Strictモードの関数を書くことができます。
これは、既存のコードとの兼ね合いを考えて利用すると良いでしょう。

:::message
関数をexportしてモジュールとして利用する場合は、
Strictモードの宣言の有無にかかわらず、Strictモードで動作します。
:::

## 特徴
Strictモードの厳格なチェック内容を見てみましょう。

:::details 1.ミスをエラーとして返す
```js: consoleで実行
(() => {
  'use strict';
  mistypeVariable = 17;
})();

// ↓エラーメッセージ↓
// Uncaught ReferenceError: mistypeVariable is not defined
//   at <anonymous>:3:19
//   at <anonymous>:4:3
```
:::

:::details 2.例外を発生させる
```js: consoleで実行
(() => {
  'use strict';
  // 書き換え不可能なグローバル変数への代入
  undefined = 5; // TypeError(例外処理) を投げます
})();

// ↓エラーメッセージ↓
// VM290:4 Uncaught TypeError: Cannot assign to read only property 'undefined' of object '#<Window>'
//  at <anonymous>:4:13
//  at <anonymous>:5:3
```
:::

:::details 3.削除できないプロパティの削除操作に対してエラーを返す
```js: consoleで実行
(() => {
  'use strict';
  delete Object.prototype; // TypeError(例外処理) を投げます
})();

// ↓エラーメッセージ↓
// VM47:3 Uncaught TypeError: Cannot delete property 'prototype' of function Object() { [native code] }
//  at <anonymous>:3:3
//  at <anonymous>:4:3
```
:::

:::details 4.関数の引数名が一意であることを必須とする
```js: consoleで実行
(() => {
  'use strict';
  function sum(a, a, c) { // !!! 構文エラー
    'use strict';
    return a + a + c; // このコードが実行されると
  }
})();

// ↓エラーメッセージ↓
// Uncaught SyntaxError: Duplicate parameter name not allowed in this context
```
:::

:::details 5.プリミティブ値にプロパティを設定することを禁止する

プリミティブ値 = メソッドを持たないデータのこと。
イミュータブル(immutable) = 変更できない値のこと。

```js: consoleで実行
(() => {
  'use strict';
  false.true = '';         // TypeError
  (14).sailing = 'home';   // TypeError
  'with'.you = 'far away'; // TypeError
})();

// ↓エラーメッセージ↓
// Uncaught TypeError: Cannot create property 'true' on boolean 'false'
// Uncaught TypeError: Cannot create property 'sailing' on number '14'
// Uncaught TypeError: Cannot create property 'you' on string 'with'
```

:::

## メリット
- エラーになる一部を教えてくれる
- プログラムを高速に実行できる
- セキュアなJavaScriptコードを記述できる

## 注意点
- 全てのブラウザでサポートされていない
- ブラウザのバージョンによってもサポートが異なる
	- https://caniuse.com/?search=use%20strict

## 動画で'use strict'を学ぶ
:::details kintone Tech Channel(キンテク)を見る
@[youtube](oGda4TNdHwg)
:::

## まとめ
`use strict` はエラー該当箇所を事前に確認することができ、セキュアなコーディングができるため記載しましょう。

- スコープの使い分け
  - カスタマイズファイル数が少ない時は 全体スコープで`use strict` を記載する。(推奨)
  - 複数のファイルを連携させる複雑なカスタマイズになった際は、Strictモード有無が混在する可能性があるため、特定の関数のみに`use strict` を利用する等、Strictモードのスコープを検討する。

## チェックポイント
- [x] kintoneカスタマイズの際に、`'use strict';`を書いている意図が分かった
- [x] `'use strict';`のスコープの違いが分かった