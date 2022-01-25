---
title: "🔰 予約語"
---

## はじめに
レストランに外食する際や、旅行で宿泊する際にホテルに予約を取りますよね。
しかし、席や部屋に空きかなければ、もちろん使用できないですし、そもそも予約を取れませんよね。
同様にプログラミング言語にも、最初から予約されているキーワード「予約語」が存在します。

![](https://storage.googleapis.com/zenn-user-upload/beee7bd2d3a57f2b49e73cd1.png =400x)

## 予約語
予約語とは、**プログラミング言語自体が定義しているワードで、変数名や関数名などで使用できないキーワード**です。予約語を変数名や関数名で使用すると、スクリプトを読み込む際にコンパイルエラーが発生します。

### JavaScriptの予約語一覧
|予約語||||||||||
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| break | delete | function | return | typeof | case | do | if |switch | var |
| catch | else | in | this | void | continue | finally | instanceof | throw | while |
|default | for | new | try | with | let | debugger | const | export | class |
| extends | super | yield | import | - | - | - | - | - | - |

よく見ると、変数定義で使用している`var` `const`や、
条件分岐で使用する`if ~ else`などが予約語となっています。
[ECMAScript 2015 における予約キーワード](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Lexical_grammar#keywords)

試しに、予約語になっているワードで変数を定義して、コードを実行してみましょう。

```js:予約語を使用した宣言(NG例)
// 変数名の場合
let delete = "削除";
// -> Uncaught SyntaxError: Unexpected token 'delete'

// 関数名の場合
function delete(){
    console.log('予約語をつかった関数名');
}
delete();
// -> Uncaught SyntaxError: Unexpected token 'delete'
```

結果は、`SyntaxError(構文エラー)`となります。
つまり、予約語は変数・関数名に定義できない仕様になっています。
ただし、予約語は単体では利用できませんが、単語を組み合わせて利用することは可能です。

例えば、削除の意味を持たせたい場合は、
`〇〇_delete`や`destroy〇〇` といったワードを利用できます。

## まとめ
プログラミング言語によって、それぞれ予約されているキーワード(予約語)が存在します。
予約語単体で、変数・関数名の定義することはできませんが、他の単語と組み合わせることで、エラーを回避した変数・関数名をつけることができます。

### 🧑‍💻確認チェック
- [x] 予約語の存在を理解した
- [x] 変数・関数定義の際に予約語を定義できないことが分かった