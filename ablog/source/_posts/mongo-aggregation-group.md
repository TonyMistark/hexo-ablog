---
layout: post
title:  "MongoDB aggregation group(MongoDB 聚合)"
date:   2019-01-12 22:32:40 +0800
categories: Mongo
---

##### MongoDB 聚合

* $group语法
{ $group: { _id: <expression>, <field1>: { <accumulator1> : <expression1> }, ... } }
_id是必选字段，group主要是用来聚合分组数据，其余的字段都可以用一下字段操作：

| name      | description                                  | example                                                      |
| --------- | -------------------------------------------- | ------------------------------------------------------------ |
| $sum      | 计算总和                                     | db.collection_name.aggregate([{$group: {_id: "$user_id", sum_num: {$sum: "$likes"}}}]) |
| $avg      | 计算平均值                                   | db.collection_name.aggregate([{$group: {_id: "$user_id", avg_num: {$avg: "$likes"}}}]) |
| $min      | 获取集合中所有文档对应值的最小值             | db.collection_name.aggregate([{$group: {_id: "$user_id", min_num: {$min: "$likes"}}}]) |
| $max      | 获取集合中所有文档对应值的最大值             | db.collection_name.aggregate([{$group: {_id: "$user_id", max_num: {$max: "$likes"}}}]) |
| $push     | 在查询结果文档中返回对应字段的值             | db.collection_name.aggregate([{$group: {_id: "$user_id", books: {$push: "$book_name"}}}]) |
| $addToSet | 在结果文档中插入值到一个数组中，但不创建副本 | db.collection_name.aggregate([{$group: {_id: "$user_id", book_name: {$addToSet: "$book_name"}}}]) |
| $first    | 根据资源文档的排序获取第一个文档             | db.collection_name.aggregate([{$group: {_id: "$user_id", first_book_name: {$first: "$book_name"}}}]) |
| $last     | 根据资源文档的排序获取最后一个文档           | db.collection_name.aggregate([{$group: {_id: "$user_id", last_book_name: {$last: "$book_name"}}}]) |

###### 管道的概念

管道在Unix和Linux中一般用于将当前命令的输出结果作为下一个命令的参数。

Mongodb的局和管道将Mongodb文档在一个管道处理完毕后将结果传递给下一个管道处理。管道操作是可以重复的。

表达式：处理输入文档并输出。表达式是无状态的，只用于计算当前聚合管道的文档，不能处理其他的文档。

这里我们介绍一下聚合框架中的几个操作：

* $project: 修改输入文档的结构，可以用来重命名，增删，也可以用于创建计算结果以及嵌套文档。
* @match: 用于过来数据，只输出符合条件的文档。$match使用Mongodb的标准查询。
* $limit: 用来限制Mongodb聚合管道返回的文档数。
* $skip: 在聚合管道中跳过指定数量的文档，并返回余下的文档。
* $unwind: 将文档中的某一个数组类型字段拆分成多条，每条包含数组中的一个值。
* $group: 将集合中的文档分组，可用于统计结果。
* $sort: 将收入文档排序后输出。
* $geoNear: 输出接近某一地理位置的有序文档。

###### 管道操作符实例

* `$project`

```shell
db.article.aggregate(
    { $project : {
        title : 1 ,
        author : 1 ,
    }}
 );
```

这样的话结果中就只含有_id, title和author三个字段了, 默认情况下 ` _id` 字段是被包含的，如果想要包含  ` _id`的话操作如下：

```shell
db.article.aggregate(
    { $project : {
        _id : 0 ,
        title : 1 ,
        author : 1
    }});
```

* `$match`

```shell
db.articles.aggregate( [
                        { $match : { score : { $gt : 70, $lte : 90 } } },
                        { $group: { _id: null, count: { $sum: 1 } } }
                       ] );
```

`$match` 用于获取分数大于70小于或等于90的记录，然后符合条件的记录送到下一阶段`$group`管道操作符进行处理。

* `$skip`

```
db.article.aggregate(
    { $skip : 5 });
```

经过`$skip`管道操作符处理之后，前五个文档被过滤掉。

* `$group`

类似于SQL语句`select user_id, count(*) from mytable group by user_id`

```shell
db.contract.aggregate([
					{$match: {"group_id" : "5d3fadb41a0e4c2235de5b46"}}, 
					{$group: {_id: "$group_id", names: {$push: "$name"}}}
					])
```

首先查询出group_id对应的文档，然后通过group_id分组，最后查出names，上面的查询结果：

```shell
{ "_id" : "5d3fadb41a0e4c2235de5b46", "names" : [ "g1_name", "g2_name", "g3_name" ] }
```



