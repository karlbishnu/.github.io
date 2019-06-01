---
layout: post
title:  993. Cousins in Binary Tree
category: 알고리즘
permalink: /algorithm/:year/:month/:day/:title/
tags: [알고리즘, 프로그래밍, 자바, java, tree, easy]
comments: true
---
[993. Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree/)
Acceptance 52.7%

* TOC
{:toc}

### NOTE
블로그라기 보다는 생각나는 생각나는 대로 두서없이 적는 낙서장이라고 보면 될것 같다.

## 2019년 4월 3일 21:00~21:30
### 문제
1. 겹치지 않는 숫자로 이뤄진 이진 트리와 두 개의 숫자가 주어진다.
2. 두 개의 숫자가 트리의 같은 레벨에 있으면서 부모가 같이 않은 경우 "사촌"이라 판단하고 true를 리턴하고 아니면 false를 리턴

### 생각 흐름 - 무식하게 풀기
1. 레벨을 알려면 BFS지, 그런데 같은 레벨이 아닌 걸 알려면?
2. 한 부모가 한 자식을 가지고 있으면 자식 노드와 null을 임의로 넣으면 된다.
3. 지금은 같은 부모만 아닌걸 판단하면 되기 때문에 아예 자식이 없는 노드는 고려할 필요가 없다.

{% gist karlbishnu/a3f879d4c69813e5776269c50fa39e2f %}
