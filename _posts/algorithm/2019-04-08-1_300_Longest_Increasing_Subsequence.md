---
title:  300. Longest Increasing Subsequence
categories:
 - Algorithm
tags: [Algorithm, 프로그래밍, 자바, java, array, medium]
---
[300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
Acceptance 40.5%

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 4월 8일 10:30~11:00
### 문제
1. 배열 내에서 순증가 부분배열 중 제일 긴 길이를 리턴


### 생각 흐름 - 무식하게 풀기
1. Algorithm 풀이 전략 230 페이의 문제
2. 많이 쓰이는 문제라고 써있어서 Leet Code에도 있을거라 생각하고 찾음
3. 아래의 예를 통해서 완전히 같은 문제임을 확인
```
Input: [10,9,2,2,5,3,7,101,18]
Output: 4
```
4. 모든 부분 배열을 발생 시키고 그 중 가장 긴 배열의 길이 값 리턴 $O(n^2)$
{% gist karlbishnu/c1efb131809144198c968b030f7ed440 %}
5. 메모이제이션으로 중복 계산이 제거 된 버전 $O(n^2)$
{% gist karlbishnu/436a3b343a68dd22ede38127419c1190 %}

## 2019년 4월 8일 13:48~15:50
6. 오늘의 본론: $O(n\log{n})$을 짤 수 있는가??
7. 이번에도 $O(n^2)$이고, 메모를 쓰긴 하는데, 메모의 방향이 틀림.
8. 재귀 방식은 끝까지 갔다가 올라오면서 메모를 해서 0번째 인덱스에 최종값이 있지만, 이번에는 메모의 가장 큰 인덱스에 최종값이 있다.
9. 왜냐하면, 값 배열에서 현재의 인덱스보다 이전 인덱스의 값들이 작을 때마다 메모에서 이전 인덱스의 값과 비교하기 때문이다.
10. 장점: 재귀 호출의 비용인 추가 콜스택 생성 없음 -> 메모리 절약, 디버그 편함
{% gist karlbishnu/34d4801fd2ea93693e33d2eae37be6eb %}
11. 환장 하겠네;; "Algorithm 풀이 전략"의 설명만으로는 도대체 어떻게 돌아가는건지 감이 안와서 leet code 솔루션 봤는데.... 신기방기하지 이해를 못하겠다 ㅠ_ㅠ
어떻게 저런 발상이!!!??
{% gist karlbishnu/d259c8757e2e4eb971b6f85361eee134 %}
