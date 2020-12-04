+++
slug = "tips-vanilla-javascript-lodash-accumulate-dictionary"
image = "d6afde5c20e6612530bd8afaf1695704.png"
title = "Vanilla JS と Lodash で連想配列を累計する"
publishDate = 2020-12-04T12:59:28.364Z
lastmod = ""
tags = ["Tips", "JavaScript", "Lodash"]
weight = 0
googleAds = true
+++
## 1. はじめに

　本記事では，JavaScript を用いて以下ような連想配列を累計する方法について考えます。様々な実装方法が考えられますが，本記事では Vanilla JS を用いた方法とユーティリティライブラリである [Lodash](https://lodash.com/) を用いた方法について記述します。

```bash
# 処理前

[
    { date: '2020-01-01', sales: 100 },
    { date: '2020-01-02', sales: 200 },
    { date: '2020-01-03', sales: 300 },
]

# 処理後

[
    { date: '2020-01-01', sales: 100 },
    { date: '2020-01-02', sales: 300 },
    { date: '2020-01-03', sales: 600 },
]

```

　本記事内で行っている作業は以下の環境下で実行したものです。また，Node.js や Lodash はインストール済みの前提で記述しており，インストール手順は割愛していることをご了承ください。

* Lodash Ver.4.17.20
* Node.js Ver.12.18.3
* Zorin OS 15.2 Core (Ubuntu 18.04 LTS)

## 2. Vanilla JS

```js {linenos=table}
const after = before.reduce((acc, cur, idx) => {
    if (acc.length) {
        cur.sales += acc[idx - 1].sales;
    }
    acc.push(cur);
    return acc;
}, []);

console.log(after);
```

```bash
$ node app.js
[
  { date: '2020-01-01', sales: 100 },
  { date: '2020-01-02', sales: 300 },
  { date: '2020-01-03', sales: 600 }
]
```

## 3. Lodash



## 4. おわりに


