# Zenn CLI

* [📘 How to use](https://zenn.dev/zenn/articles/zenn-cli-guide)

### 使い方

1. git clone
   1. `git clone https://github.com/naberina/MannerBooks.git`
2. npm install
   1. `cd MannerBooks && npm install`
3. npx zenn preview
   1. `npx zenn preview`
4. ローカル環境でプレビュー
   1. `localhost:8000`

### 全体像

```
.
├── articles
├── books
│   └── imoni-manner-book // いもキャン御作法本
│        ├──1.imoni-manner-book.md //チャプター毎の記事
│        ├──2.imoni-manner-book.md
│        ├──3.imoni-manner-book.md
│        ├──4.imoni-manner-book.md
│        ├──n.imoni-manner-book.md
│        └──10.imoni-manner-book.md
├── README.md
├── .gitignore
├── package.json
└── package-lock.json
```

