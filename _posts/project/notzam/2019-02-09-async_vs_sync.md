---
layout: post
title: Async vs Sync
category: Project
permalink: /project/:year/:month/:day/:title/
tags: [프로젝트, 프로그래밍, 파이썬, python, async, sync]
comments: true
---

* TOC
{:toc}

## 비동기 vs 동기

mingrammer님이 번역하신 [비동기 파이썬](https://mingrammer.com/translation-asynchronous-python/)를 다시 한 번 보면서 생각을 했다.

비동기가 멋져보이는 것은 사실이라 나도 몇일 동안 알고싶어서 보고 또 보고 고민했다.

근데 결론은, **지금 내 프로젝트에서 쓸 수 있나?** 로 결정해야한다.

### 비동기 장점
- 뭔가 있어 보인다.
- 새로운 것을 공부하고 적용해 보는 재미가 있다.

### 비동기 단점
- [비동기 파이썬](https://mingrammer.com/translation-asynchronous-python/)에 설명 돼있는데 좀 치명적이다. **모든 코드가 비동기**로 돼있어야한다.
    - 내가짜는 코드는 그렇다 치더라도, 핵심이 되는 [TensorFlow](https://www.tensorflow.org/) API 및 [Keras](https://keras.io/)가 파이썬 3.4의 기능인 async await를 썼는지 혹은 최소한 이벤트루프를 블로킹하지 않게 됐는지가 중요하다.
- 많은 삽질이 예상된다. (끝날 시기를 가늠하기 힘들다.)

### 동기 장점
- 코드가 읽기 쉽다.
- 익숙하다.

### 동기 단점
- 프로세스의 개수가 늘어난다.
- 이에 따라서 도커 개수도 늘어난다.

---

## 결론
쓰면서 결론 냈다. 동기식으로 구현한 후에 비동기식으로 전환해 본다.
