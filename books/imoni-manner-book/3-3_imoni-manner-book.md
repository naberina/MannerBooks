---
title: "🔰 変数"
---
## 変数とは？
プログラミングには、文字列や数値データに名前をつけて、
値を繰り返し利用できるようにする**変数**という機能があります。

![](https://storage.googleapis.com/zenn-user-upload/da7dbed88e8299849a5dab09.png =400x)

変数を定義するには、 `const` `let` `var`といった変数宣言のキーワードを使用して変数を定義します。

```javascript:OK例
const 変数名 = 初期値;
let 変数名 = 初期値;
var 変数名 = 初期値;
```

変数定義時に`const` `let` `var`を付けなかった場合は、グローバル変数として定義されます。ただし、グローバル変数は、スコープが分かりにくくなる可能性が高くなるほか、既存の値を上書きする可能性が高くなります。必ず変数定義を忘れずに行いましょう。

```javascript:NG例
変数名 = 初期値;
// -> Global変数に定義される
```

### 変数に代入できるデータ
変数には、文字列や数値、配列、オブジェクトなどを代入することができます。
もっと言うと、関数なども変数に代入することができますが、ここでは、**変数は何かしらの値に名前をつけて代入しておくことができる・繰り返し利用できる**ということを理解しておきましょう。
![](https://storage.googleapis.com/zenn-user-upload/e21f049d54e18eb8e57bcb86.png)

## 変数定義の違いを理解しよう
先程、変数定義の際は`const` `let` `var`をつけると紹介しましたが、この3つの定義は何が異なるのか確認していきましょう。

まず、変数の違いを理解する前に、重要な2つのキーワード
**再代入**と**再定義**を説明します。

### 再代入
読んで字の如く...なのですが、**一度定義した変数に再び別の値を代入すること**です。
例を見てみましょう。

```js:再代入(var)
var number = 0;
console.log(number);
// -> 0

number = 10;
console.log(number);
// -> 10
```

```js:再代入(let)
let number = 0;
console.log(number);
// -> 0

number = 10;
console.log(number);
// -> 10
```

```js:再代入(const)
const number = 0;
console.log(number);
// -> 0

number = 10;
console.log(number);
// -> Uncaught TypeError: Assignment to constant variable.
```

`var`と`let`で定義した場合は、numberの値が上書きされていることが分かります。
ただし、「`const`で定義した変数は上書きできないよ！」と言ったエラーメッセージが表示されています。

### 再定義
こちらも読んで字の如くなのですが、**一度定義した変数名を再び利用して変数を定義すること**です。
例を見てみましょう。

```js:再定義.js(var)
var number = 0;
console.log(number);
// -> 0

var number = 10;
console.log(number);
// -> 10
```

```js:再定義.js(let)
let number = 0;
console.log(number);
// -> 0

let number = 10;
console.log(number);
// -> Uncaught SyntaxError: Identifier 'number' has already been declared
```

```js:再定義.js(const)
const number = 0;
console.log(number);
// -> 0

const number = 10;
console.log(number);
// -> Uncaught SyntaxError: Identifier 'number' has already been declared
```

今回は、`var number`はnumberの再定義が行われましたが、
`let` `const`はSyntaxError(構文エラー)が表示され、既に定義されている変数名は再定義ができないことが分かります。

ここまでくると、それぞれの違いがわかってきますよね。

### 変数定義の違い

|変数名|再代入|再定義|メモ|
|:--|:--|:--|:--|
|`var`|可|可|推奨されていません。同じ名前の変数を再定義できてしまうため、意図せず上書きしてしまう可能性が高くなる|
|`let`|可|不可|値の変更がある変数名を定義する際に利用する|
|`const`|不可|不可|値の変更をしない変数名を定義する際に利用する|

`var`は、`const`か`let`で置き換えて定義しよう！

### 定数 `const`
定数はコンスタントケース(CONSTANT_CASE)で定義します。
https://cou929.nu/data/google_javascript_style_guide/

- `const`
	- 再代入できない変数
	- 必ずしも定数ではない

```javascript
//**********//
// 定数の例
//**********//
const TEN_NUMBER = 10;
// TEN_NUMBERという変数は常に10という値を示す
//-> 定数と呼んでも正しい

//**********//
// NOT 定数の例
//**********//
const object = {
    key: "値"
};

object.key = "新しい値"; // key: '値'が再代入できてしまう
// オブジェクトそのものが変更できてしまう
//-> 値を上書きできるため、定数と呼べない
```

## まとめ
変数宣言をしないとJavaScriptはグローバル変数として認識してしまします。
(`use strict`を利用している場合はエラーが返る)
繰り返し利用する値は、必ず変数宣言をしてデータを扱いましょう。

# 🧑‍💻 チェックポイント
- [x] const, let, varの違いが分かった
- [x] 再代入と再定義を自分の言葉で説明できる