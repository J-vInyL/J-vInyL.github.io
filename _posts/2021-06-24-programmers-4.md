---
title: 프로그래머스 가장 큰 수 Javascript
description: 프로그래머스 코딩테스트 연습
categories: Algorithm
tags: Programmers
---

## 프로그래머스 가장 큰 수 Javascript

> 정렬 알고리즘을 이용하여 풀이

[문제 사이트 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42746)

**처음 문제를 봤을땐 하나하나 숫자들을 꺼내서 조합을 해줘야 되나 생각했지만 문제를 다시 읽어보니 생각해낸 풀이**

1. 문자열로 리턴을 해주니깐
2. 각 숫자들을 문자로 변환
3. 문자로 변환된 숫자를 비교정렬
4. 문자열들을 합치기 join("")
5. numbers 배열이 0으로만 구성되어 있으면 0만 출력하기

```
function solution(numbers) {
  var answer = numbers
    .map(c => c + "")
    .sort((a, b) => b + a - (a + b))
    .join("");

  return answer[0] === "0" ? "0" : answer;
}
```

![체첨 통과](./../_site/photos/21-06-24-1.png)
