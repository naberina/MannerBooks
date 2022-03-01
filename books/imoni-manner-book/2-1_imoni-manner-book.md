---
title: "🍵 インデント"
---

## はじめに
普段みなさんは、文章を書くときに段落ごとに字下げを行いますよね。
(※かくいうこの文章は、字下げされていないのですが...)
同様にプログラミングでも、コードの可読性(読みやすさ)を高めるために字下げ(インデント)を行います。

![](https://storage.googleapis.com/zenn-user-upload/b767b552714051a0f64515ac.png =400x)

「数行程度のコードなら、多少インデントが崩れていても読めるし気にしない」といったスタンスはよろしくありません。
なぜかと言うと、コードをチームメンバーに引き継いだときや、数ヶ月後の自分がコードを修正したいときに、コードが読みにくいと
- 解読するのに時間がかかる
- 関数のまとまりが分かりにくい
- インデントを無視したコードを増加させる
などの負のサイクルがうまれてしまいます。

そのため、数行のコードでも、必ずインデントを守ってコーディングしましょう！

# インデントスタイルの基本

[cybozu developer network](https://developer.cybozu.io/hc/ja/articles/360028177472)のサンプルコードは、**半角スペース2つ分**のインデントを取っています。

```javascript:sample.js
let body = {
  'app': kintone.app.getId(),
  'id': 1001
};

kintone.api(kintone.api.url('/k/v1/record.json', true), 'GET', body, function(resp) {
  console.log(resp);
}, function(error) {
  console.log(error);
});
```

|参考サイト|インデント数|
|:--|:--|
|[cybozu developer network](https://developer.cybozu.io/hc/ja/articles/360028177472)|半角スペース2つ|
|[JavaScript Standard Style](https://standardjs.com/rules.html)|半角スペース2つ
|[Google](https://cou929.nu/data/google_javascript_style_guide/#id41)|- 変数、オブジェクト、配列: 半角スペース2つ <br> - 関数: 半角スペース4つ|

こちらはあくまで参考値ですが、半角スペース2つを利用している企業やプロジェクトが多いです。ただし、既存のコードが半角スペース4つ分のインデントであれば、そのルールに統一した方が良いです。それぞれの、プロジェクトのルールに合わせて正しくインデントを行いましょう！

## 自動インデント修正
コーディングをする際に、[VSCode](https://code.visualstudio.com/)などのエディタを利用している場合は、コード整形ツール(Formatter)をインストールすることで、自動でインデント調整をすることができます。お使いのエディタでインデント設定があるか確認してみてください。

:::message alert
[JSEdit for kintone](https://developer.cybozu.io/hc/ja/articles/205452653-JSEdit-for-kintone)をご利用の場合は、自動インデント修正はありません。ご了承ください。
:::

### ※VSCodeの場合

1. Formatterをインストールする
  - [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
2. ショートカットキーを使って自動インデント修正

|PC|ショートカットキー|
|--|--|
|Mac|Shift + option + F|
|Windows|Shift + Alt + F|

![](https://storage.googleapis.com/zenn-user-upload/d59b0cf8cc37580a04e2baef.gif)

# まとめ
- コーディングする際は、コードの可読性を高めるためインデントを必ず整えよう
# チェックポイント
- [x] インデントの重要性が分かった
- [x] 使用しているエディタに自動インデント修正機能が存在するか確認できた
- [x] 現在カスタマイズしているコードが正しくインデントできた
