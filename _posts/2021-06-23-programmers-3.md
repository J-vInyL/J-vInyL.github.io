---
title: 프로그래머스 k번째 수 Javascript
description: 프로그래머스 코딩테스트 연습
categories: Algorithm
tags: 프로그래머스
---

## 프로그래머스 k번째 수 Javascript

> 정렬을 이용하여 원하고자 하는 숫자를 배열에서 찾기

[문제 사이트 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42748)

- 저번에 활용한 2차원 배열을 이용하여 문제를 풀음

  **처음 생각한 코드**

```
function solution(array, commands) {
  var answer = [];
  var com = commands.length;
  var copyary = [];

  for (var i = 0; i < com; i++) {
    var start = commands[i][0] - 1;
    var end = commands[i][1];
    var search = commands[i][2] - 1;
    copyary = array.slice(start, end).sort();
    //console.log("test", answer);
    answer.push(copyary[search]);
  }
  return answer;
}
```

![체첨 통과 실패](./../_site/photos/21-06-23-1.png)

_아마 공간복잡도를 생각안하고 설계를 해서 통과 가 안된 모양이다..ㅠ_

**다시 생각한 코드**

```
function solution(array, commands) {
 var answer = [];

 for (var i = 0; i < commands.length; i++) {
   var copyary = array
     .slice(commands[i][0] - 1, commands[i][1])
     .sort((a, b) => {
       return a - b;
     });
   answer.push(copyary[commands[i][2] - 1]);
 }

 return answer;
}
```

_**내가 생각한 코드에서 변수들과 메소드들을 합치니 통과가 되었다.**_
