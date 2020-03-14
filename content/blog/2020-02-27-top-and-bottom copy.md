---
title: "記事２"
date: 2020-02-27T07:31:54+09:00
lastmod: 2020-02-27T07:31:54+09:00
comments: true
category: ['Tech']
tags: ['Tableau']
published: true
slug: article-2
img: https://res.cloudinary.com/meganii/image/upload/c_scale,f_auto,q_auto,w_75/v1579905055/thumb_tableau_czhjxd.png
---

上位N個もしくは下位N個を個別で表示することは`ディメンションフィルター`を利用することで比較的簡単に実装できます。

しかし、上位N個と下位N個を1つのグラフ上に表現する場合はちょっとした工夫が必要でしたので、メモしておきます。



## カテゴリ別の上位と下位Nを表示する方法

### True / Falseを返す計算フィールドを作成する

`N Parameter`というパラメータを作り、以下の`計算フィールド`を作成します。名前は、`Top & Bottom N Filter`としました。

```sql
RANK( SUM( [売上] ), 'desc' ) <= [N Parameter]
OR 
RANK( SUM( [売上] ), 'asc' ) <= [N Parameter]
```

上記の計算では、昇順または降順でSUM([売上])が上位Nのサブカテゴリに入る場合、trueの値を返します。


```bash
_token=$1

post_data='{ "build_parameters": { "BUNDLE_UPDATE": "true" } }'

curl \
--header "Accept: application/json" \
--header "Content-Type: application/json" \
--data "$post_data" \
--request POST https://circleci.com/api/v1/project/meganii/meganii.com/tree/master?circle-token=${_token}

```
