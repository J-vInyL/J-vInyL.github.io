---
title: 프로그래머스 위장 Javascript
description: 프로그래머스 코딩테스트 연습
categories: Algorithm
tags: 프로그래머스
---

## 프로그래머스 위장 Javascript

> 해시를 이용하여 문제를 풀었지만 처음엔 배열로 풀려고 하여 시간이 좀 걸림

[문제 사이트 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42578)

처음 생각한 코드

- 하나의 예시에서는 성공이 되지만
- 다른 하나의 예시에서는 실패가 되어 다시 생각함

```
function solution(clothes) {
  var answer = 0;
  var wear = clothes.length;

  for (var i = 0; i < wear; i++) {
    if (clothes[0][1] === clothes[i][1]) {
      var wear_a = i;
      //var wear_b = wear - wear_a;
    } else if (clothes[0][1] !== clothes[i][1]) {
      var wear_b = wear - wear_a;
    }
  }

  answer = wear_a + 1 * (wear_b + 1);

  return answer - 1;
}
```

다시 생각한 코드

- 객체를 이용하여 key 와 value 해시를 이용하여 풀이

```
function solution(clothes) {
  var answer = 1;
  var obj = {};
  for (var i = 0; i < clothes.length; i++) {
    obj[clothes[i][1]] = (obj[clothes[i][1]] || 1) + 1;
  }

  for (var key in obj) {
    answer *= obj[key];
  }

  return answer - 1;
}
```
