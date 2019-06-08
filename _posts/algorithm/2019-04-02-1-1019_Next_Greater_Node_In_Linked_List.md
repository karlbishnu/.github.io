---
layout: post
title:  1019. Next Greater Node In Linked List
category: Algorithm
permalink: /algorithm/:year/:month/:day/:title/
tags: [Algorithm, 프로그래밍, 자바, java, linked list, stack, medium]
comments: true
---
[1019. Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/)
Acceptance 55.9%

* TOC
{:toc}

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 4월 2일 15:40~17:00
### 문제
1. 링크드 리스트가 주어지고,
2. 각 노드의 숫자 크기는 무작위
3. 배열을 리턴 하는데, 각 인덱스의 노드 보다 뒤에 나오는 큰 수를 리턴
4. 그 수보다 큰 수가 없다면 해당 배열 요소 값은 0

### 생각 흐름 - 무식하게 풀기
1. Stack이네..
2. 링크드 리스트를 한번 순회하면서 stack에 push
3. 다 돌았으면 답이 될 배열 초기화
4. 배열의 마지막 값은 무조건 0 이고,
5. stack에서 pop 하면서 최대값과 비교해서 작으면 하고 해당 배열 값을 세팅
6. 아니면 배열 값은 0 이고 최대값 갱신
7. 결과 리턴
8. 시간 복잡도 $O(n)$
9. 망할... 어쩐지 -\_- 너무 쉽다 했어...
10. 문제도 잘못 읽고, 예제도 부실하네
11. 위 코드는 아래 예제 충족 못함
```python
case :   [1,6,5,4,3,2,1,2,3,4,5,6,7]
answer : [6,7,6,5,4,3,2,3,4,5,6,7,0]
```

### 다시 생각하기
1. 리스트를 스택에 쌓은 후 배열 (a)로 변환
2. 결과 배열 (res) 생성
```java
  for(int i=a.length-2, j=a.length-1; i>=0; i--, j--){
    a[j] = stack.pop();
    res[i] = nextLarger(a, j, stack.peek());
  }
  //...
  int nextLarger(int[] a, int s, int target){
    int res = 0;
    for(; s<a.length; s++){
      if(target<a[s]){
          res = a[s];
          break;
      }
    }
    return res;
  }
```

{% gist karlbishnu/75711956bec185f15c649f6ff63f299d %}

## 2019년 4월 3일 10:02~10:27
1. 음... 상당히 느리군.... 123 ms, faster than 26.57%;;
2. 사실 stack을 pop했을 때 배열 a의 [j..a.length-1]사이의 값 중 pop한 값보다 작으면 더이상 필요 없어지는 건데....
3. a를 배열이 아니고 stack으로 교체해서 2. 작업을 하도록 변경해볼까?
4. 많이 빨라졌다. 20 ms, faster than 86.25%
{% gist karlbishnu/7ce3042eece00fdad0fe5e818ce8d040 %}
