---
title:  925. Long Pressed Name
categories:
 - Algorithm
tags: [Algorithm, 프로그래밍, 자바, java, string, easy]
---
[925. Long Pressed Name](https://leetcode.com/problems/long-pressed-name/)
Acceptance 44.2%

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 4월 3일 20:21~20:50
### 문제
1. 진짜 이름과 타이핑 된 문자열이 주어진다.
2. 타이핑 된 문자열에 같은 문자가 오래 눌려서 타이핑 됐는지 여부를 판단하라. 문자열이 같아도 true임.

### 생각 흐름 - 무식하게 풀기
1. 문자열 관련 문제를 좀 중점적으로 보려는데 흠... 좋아 보이는 문제를 찾기 힘드네
2. 당장 떠오르는 것은, 각 문자열의 인덱스를 움직이면서 검사하는데, 타입된 문자열의 인덱스를 먼저 움직여서 해당 문자열의 중복 입력 된 수를 세고, 진짜의 인덱스를 움직이면서 문자를 셈한다.
3. 중복 수가 진짜 수보다 크거나 같으면 계속 진행. 아니면 false
4. 두 문자열 다 훑어봤는지 여부에 따라 결과 리51

{% gist karlbishnu/4bb0544e695096b79fb9c3794d8dffb1 %}
