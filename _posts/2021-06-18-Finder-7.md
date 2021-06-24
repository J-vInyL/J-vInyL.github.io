---
title: MongoDB Mongoose & Node.js 데이터 수정(업데이트)
description: React Express MongoDB 활용
categories: 개인프로젝트
tags: Finder
---

## MongoDB Mongoose Update(수정) 기능

> 프로젝트에 있어 CRUD 중 Update 기능 구현

액션이 들어오면 수정 해야 할 데이터를 불러온 후 수정된 데이터들을 새롭게 업데이트 해준다.

- axios를 활용하여 http 통신과 서버에서 처리해줘야 할 쿼리를 보내줄수 있다.

- 쿼리들을 이용하여 DB 데이터 들을 업데이트

> update 메소드는 기본옵션으로 단 하나의 document를 수정한다.

1.  특정 필드 업데이트 하기
    - 특정 field의 값을 수정 할 땐 **\$set** 연산자를 이용
2.  document를 replace 하기
    - ```
        db.schema.update( { name: "ABC" }, { "name": "ABCDE", age: 2 })
      ```
      새로운 document로 replace 할땐 id 값은 바뀌지 않는다.
3.  특정 field 제거하기

    - 특정 field를 제거 하기위해선 **\$unset** 연산자를 이용하여 제거가능

4.  존재하지 않는 document 를 새로 추가하기
    - 찾고자하는 document 가 존재 하지 않으면 **upsert** 연사자를 설정하여 추가 가능

> 프로젝트에서는 update 해야할 field들이 많아 \$set 연산자를 사용하여 처리함

```
Product.update(
    { _id: { $in: req.body.id } },
    {
      $set: {
        field1 : data
        field2 : data
        field3 : data
      }
```
