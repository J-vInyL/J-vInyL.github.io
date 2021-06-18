---
title: MongoDB Mongoose & Node.js 데이터 삭제
description: React Express MongoDB 활용
categories: 개인프로젝트
tags: Finder
---

## MongoDB Mongoose Delete(삭제) 기능

> 프로젝트에 CRUD 중 Create 와 Read만 있어 추가하기위해 Delete 기능도 추가함

기존에 product들은 고유한 ID로 쿼리를 넘겨주어 받아왔다.

- axios 로 http 통신을 유지하고 있으므로 기존 코드만 조금 수정하면 삭제 부분도 쉽게 만들수 있었다.

- ID를 쿼리로 날려주어 서버에서 삭제를 하게끔 유도

- 통신이 완료되면 최상위 경로로 가기

`코드 예시`

```
axios.delete(`/api/product/products_by_id_delete?id=${productId}`
      .then(alert("삭제 완료"));
    props.history.push("/");
```

- 서버부분에서 express로 요청을 받으면 몽고DB의 쿼리를 이용하여(deleteOne) 작업을 하였다.
- 몽고DB는 롤백을 지원하지않아 oplog를 사용하여 어떤 쿼리를 실행했는지 기록으로 남겨두어, 그 기록을 거꾸로 돌리면 롤백과 유사한 효과를 볼 수 있다.
- Remove 메소드가 있지만 몽고DB 최신 버전은 DeleteOne, DeleteMany 대체하는 메소드가 있으므로 사용하였다.
- **DeleteOne** : 매칭되는 첫 번쨰 도큐먼트만 지운다.
- **DeleteMany** : 매칭되는 모든 도큐먼트를 지운다

> 예시 DeleteOne

```
db.schema.DeleteOne({ name : 삭제할 이름})
```

> Delete 쿼리를 이용함

```
router.delete("/products_by_id_delete"  req, res

Product.deleteOne({ _id: { $in: req.query.id } }).exec();
```
