---
title: 프로그래머스 H-index Javascript
description: 프로그래머스 코딩테스트 연습
categories: Algorithm
tags: Programmers
---

## 프로그래머스 H-index Javascript

> 정렬 알고리즘을 이용하여 풀이

[문제 사이트 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42747)

**문제를 잘못이해해서 많이 시간을 잡아먹었던 문제 ㅠ..**

```
function solution(citations) {
    var answer = 0;
    citations.sort((a,b) => b-a)

    while(answer + 1 <= citations[answer]){
        answer ++
    }

    return answer;
}
```

_**처음 문제만 잘 이해했다면... 위키백과를 들어가도 무슨말인지 이해가 잘 안된건 사실...**_
