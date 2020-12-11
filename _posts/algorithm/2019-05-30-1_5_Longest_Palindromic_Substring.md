---
title:  5. Longest Palindromic Substring
categories:
 - Algorithm
tags: [Algorithm, 프로그래밍, 자바, java, String, medium]
---

[5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
Acceptance 27.3 %

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 5월 30일 19:30~21:00
### 문제
주어진 문자열에서 가장 긴 회문 리턴 (복수인 경우 아무거나)

### 생각 흐름
1. 오랜만의 문제 풀이
2. 머리가 녹슬었는지 요상한 풀이법 밖에 생각나지 않아서 가장 기본이 되는 무식하게 풀어보고 제출 했다.

{% gist karlbishnu/26e57ba9d45422dd2d99a0a38b58a359 %}

```
Runtime: 929 ms, faster than 5.37% of Java online submissions for Longest Palindromic Substring.
Memory Usage: 35 MB, less than 99.94% of Java online submissions for Longest Palindromic Substring.
```
3. 통과는 했는데 만족스럽진 않음;;
4. 문자열을 뒤집어서 한 글자씩 겹치게 지나가면서 가장 긴 구간을 검출하는 법을 생각하긴 했는데....
5. 아이패드에서 녹화하고 GIF로 만들려다가 시간 다가네;;
<center>
<figure>
<img src="/assets/post-img/algorithm/190530-1.gif" alt="views" />
</figure>
</center>

## 2019년 6월 1일 14:00~15:00
1. 다시 보니깐 너무 단순하게 생각했네;; GIF 한번 만들어본다고 너무 집중했었나... 양 끝에 가장 긴 회문이 있지 않는 이상 위의 생각은 정답을 못찾음..
2. 역시 DP가 답인듯
3. 회문은 양끝의 문자열에서 양끝 문자열이 같고, 그 외의 문자열이 회문이어야 한다. 그러므로 재귀함수로 정의가 가능하다.
4. 기저 조건으로는 재귀함수로 패스한 시작 인덱스가 끝 인덱스보다 크거나 같으면, 각각 빈 문자열이거나 단일 문자이므로 true

{% gist karlbishnu/0cc8d9c0db792f82afd0919196587568 %}

```
Runtime: 189 ms, faster than 14.58% of Java online submissions for Longest Palindromic Substring.
Memory Usage: 50.9 MB, less than 5.01% of Java online submissions for Longest Palindromic Substring.
```

5. 실행속도가 929ms -> 189ms 4.9배 빨라졌는데도 14.58%에 있네;; 메모리 수준도 참담하군 ㅋㅋ
6. 오래된 문제인만큼 많이 최적화해서 제출됐나보네.
