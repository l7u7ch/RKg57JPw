+++
slug = "tips-vanilla-javascript-lodash-accumulate"
image = "d6afde5c20e6612530bd8afaf1695704.png"
title = "Vanilla JS と Lodash で累計する"
publishDate = 2020-12-04T10:23:18.620Z
lastmod = ""
tags = ["Tips", "JavaScript", "Lodash"]
weight = 0
googleAds = true
+++
## 1. はじめに

　本記事では，以下のデータ処理を JavaScript で行う方法について考えます。様々な実装方法が考えられますが，本記事では Vanilla JS を用いた方法とユーティリティライブラリである [Lodash](https://lodash.com/) を用いた方法について記述します。

```bash
# 処理前

[
    { date: '2020-01-01', sales: 100 },
    { date: '2020-01-02', sales: 100 },
    { date: '2020-01-03', sales: 100 },
]

# 処理後

[
    { date: '2020-01-01', sales: 100 },
    { date: '2020-01-02', sales: 200 },
    { date: '2020-01-03', sales: 300 },
]

```

　本記事内で行っている作業は以下の環境下で実行したものです。また，Node.js や Lodash はインストール済みの前提で記述しており，インストール手順は割愛していることをご了承ください。

* Lodash Ver.4.17.20
* Node.js Ver.12.18.3
* Zorin OS 15.2 Core (Ubuntu 18.04 LTS)

## 2. Vanilla JS

```js
const before = [1, 2, 3]

const after = before.reduce(
    (acc, cur, idx) => [...acc, cur + (acc[idx - 1] || 0)], []
);

console.log(after);
```