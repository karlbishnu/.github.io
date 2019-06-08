---
layout: post
title:  1021. Best Sightseeing Pair
category: Algorithm
permalink: /algorithm/:year/:month/:day/:title/
tags: [Algorithm, 프로그래밍, 자바, java, dp, dynamic programming, medium]
comments: true
---
[1021. Best Sightseeing Pair](https://leetcode.com/problems/best-sightseeing-pair/)
Acceptance 42.9%

* TOC
{:toc}

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 3월 26일 16:25~16:45
### 문제
배열에서 가장 큰 $A[i] + A[j] + i - j$값을 리턴
### 생각 흐름
1. 결과 결정하는 요소가 두 개다. 배열의 두 값, 그 두 사이의 거리.
2. 배열의 두 값을 최대한으로 높이고, 가까운게 좋다.
3. 그러면 둘 중 한 값은 무조건 배열의 최대값인가? - 유리한 것은 사실이나, 참은 아니다.
4. 최대값을 기점으로 오른쪽 왼쪽으로 나누고 왼쪽에서 가장 큰 결과, 오른쪽에서 가장 큰 결과를, 걸쳐있을 때의 가장 큰 결과를 재귀적으로 구하고 셋 중 가장 큰 값을 리턴??

## 2019년 3월 26일 20:25~21:02
1. 살짝 식을 단순화 해보자...
2. i관련 값은 해당 배열의 값과 인덱스를 더한 것이고,
2. j관련 값은 해당 배열의 값에서 인덱스를 뺀 것이다.
3. 그러므로 일단 배열을 하나 선언해서 i관련 값을 구해서 세팅하고,
4. 해당 배열을 역순으로 순회하면서 해당 인덱스의 j관련 그때까지의 맥스값을 더하면서 최대값만 리턴하면 될 것 같다.
5. 이렇게 생각한 것은 j값 결과는 오른쪽에 있는 값이 최대값이라 가정했을 때 모든 배열에 영향을 끼치는 스택 구조로 생각을 했기 때문이다.
6. 공간 복잡도 및 시간 복잡도는 $O(n)$이 된다.

{% gist karlbishnu/a622de841d397f65f5a04cc3b6f4a460 %}
