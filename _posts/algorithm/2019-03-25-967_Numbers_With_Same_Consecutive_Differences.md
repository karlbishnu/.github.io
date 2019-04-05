---
layout: post
title:  967. Numbers With Same Consecutive Differences
category: 알고리즘
permalink: /algorithm/:year/:month/:day/:title/
tags: [알고리즘, 프로그래밍, 자바, java, dp, dynamic programming, medium]
comments: true
---
[967. Numbers With Same Consecutive Differences](https://leetcode.com/problems/numbers-with-same-consecutive-differences/)
Acceptance 36.1%

* [2019년 3월 25일 20:39~21:11](#2019년-3월-22일-20392111)

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 3월 25일 20:39~21:11
### 문제
N의 개수만큼 K 만큼 거리가 있는 수의 순열을 발생시키면 되나... 예제만으로는 부족해서 아래의 예를 돌려봄.
```python
N=4, K=3
[1414,1474,2525,2585,3030,3036,3630,3636,3696,4141,4147,4741,4747,5252,5258,5852,5858,6303,6363,6369,6963,6969,7414,7474,8525,8585,9630,9636,9696]
```
1. 재귀로 Set 메모랑 현재 숫자, N-1, K를 넘겨서 +-K를 시키고, Set에 이미 숫자가 있으면 끝내고, N-1이 0이 되면 Set에 넣고...
2. 맨 처음 시작하는 함수는 for문으로 i가 1부터 시작하게... 단, N=1일 때는 0부터 시작해야 함


{% gist karlbishnu/4ae8383edcaf949c0038a696f7ba6dd3 %}
