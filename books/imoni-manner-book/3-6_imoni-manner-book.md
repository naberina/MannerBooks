---
title: "🔰 関数式"
---

## 関数式
関数式は、関数自体を変数で定義した式です。
関数式は関数名を省略できます。

```javascript
const increment = function(n) {
  return n + 1;
}

console.log(increment(10));
// -> 11
```

## 関数 (ES6対応)
ES6とは、2015年から利用可能になった、JavaScriptの新しい文法です。
例えば、変数宣言が `var` だけではなく、 `const` `let` が使用できるようになったり、アロー関数 `() =>` や、非同期処理(promise)が実装できるようになりました。

### 関数を変数に入れる
関数の戻り値を受け取るために、関数の結果を変数に代入していきます。

```javascript
function increment(n) {
  return n + 1;
}

let result =  increment(10);
console.log(result);
// -> 11
```

## 関数式
関数式は、関数自体を変数で定義した式です。
関数式は関数名を省略できます。

```javascript
const increment = function(n) {
  return n + 1;
}

console.log(increment(10));
// -> 11
``` -->