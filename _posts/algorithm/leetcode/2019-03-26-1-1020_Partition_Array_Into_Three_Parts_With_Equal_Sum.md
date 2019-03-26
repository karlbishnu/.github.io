---
layout: post
title:  1020. Partition Array Into Three Parts With Equal Sum
category: 알고리즘
permalink: /algorithm/:year/:month/:day/:title/
tags: [알고리즘, 프로그래밍, 자바, java, dp, dynamic programming, easy]
comments: true
---
[1020. Partition Array Into Three Parts With Equal Sum](https://leetcode.com/problems/partition-array-into-three-parts-with-equal-sum/)
Acceptance 45.9%

* [2019년 3월 26일 14:45~15:04](#2019년-3월-26일-14451504)

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 3월 26일 14:45~15:04
### 문제

1. 배열을 임의로 세 부분으로 나눌 때, 왼쪽합, 가운데 합, 오른쪽합이 같은 지점이 있으면 true 없으면 false 리턴
2. 쉬운 문젠가?? 전역 검사하면 $O(N^2)$으로 한다고 하면 쉬운데.... 이 보다 줄이기가....
3. 아, 일단 한 번 다 더하고, 세 파트로 나눠졌을 때 각 파트는 1/3로 나눠져야하니깐, 3으로 나눠떨어지지 않으면 무조건 false
4. 나눠떨어지면, 다시 한 번 순회해서 1/3이 되는 지점의 수를 세면 되겠다.

{% gist karlbishnu/392b66af9f08f9cc50f85edda7450176 %}
