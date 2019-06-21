---
layout: post
title:  Asymmetric Tiling
category: Algorithm
permalink: /algorithm/:year/:month/:day/:title/
tags: [Algorithm, 프로그래밍, 자바, java, dp, dynamic programming, Algorithm 풀이 해결 전략, 구종만, P260]
comments: true
---

* TOC
{:toc}

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 4월 16일 14:30
### 문제
1. $2*n$ 크기의 직사각형에 $2*1$크기의 타일로 겹치지 않고, 좌우 대칭이 되지 않게 덮을 수 있는 경우의 수
2. $2*1$ 타일을 90도 돌려서 $1*2$로 하는 것은 가능
3. 경우의 수가 커질 수 있으므로 1000000007 으로 나머지 연산을 취한다.

```
Input: 2
Output: 0
//모든 경우가 대칭

Input: 4
Output: 2

Input: 92
Output: 913227494
```

### 생각 흐름 - 무식하게 풀기
1. 맨 왼쪽으로부터 시작해서 각각의 컬럼에 어떤방식으로 타일이 덮이는지에 따라 칸수를 더해가면서 재귀적으로 계산해나가면 됨
2. 이 때 메모도 넘기고, 타일이 붙여진 방식 (예를 들어 $2*1$ 면 0, $1*2$면 11)로 문자열을 덧붙여가고, 끝까지 가면 문자열이 회문(Palindrome)인지 검사하여 아닐 때만 카운트 하도록 하면 될 듯

{% gist karlbishnu/32adca1fef730c88f9b8c4a6df64706f %}
