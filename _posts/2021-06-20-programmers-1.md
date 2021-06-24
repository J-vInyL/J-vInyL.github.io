---
title: 프로그래머스 다리를 지나는 트럭 Javascript
description: 프로그래머스 코딩테스트 연습
categories: 알고리즘
tags: 프로그래머스
---

## 프로그래머스 다리를 지나는 트럭 Javascript

> Queue 알고리즘을 이용하여 풀이

[문제 사이트 바로가기](https://programmers.co.kr/learn/courses/30/lessons/42583)

```
function solution(bridge_length, weight, truck_weights) {
    let queue = [];
    let answer = 0;
    let sum = 0;


    for(let i =0;i<bridge_length;i++){
        queue.push(0);
    }


    let now_truck = truck_weights.shift()

    queue.unshift(now_truck)
    queue.pop()

    sum += now_truck

    answer++


    while(sum){
        sum -= queue.pop()

        now_truck = truck_weights.shift()

        if(now_truck + sum <= weight){
            queue.unshift(now_truck);
            sum += now_truck;
        } else{
            queue.unshift(0)
            truck_weights.unshift(now_truck)
        }
        answer++;
    }

     return answer;
    }


```
