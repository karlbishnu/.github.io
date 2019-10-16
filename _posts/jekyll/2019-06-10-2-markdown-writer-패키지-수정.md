---
layout: "post"
title: "Markdown Writer 패키지 수정"
date: "2019-06-10 17:10"
permalink: "/Jekyll/:year/:month/:day/:title/"
category: "Jekyll"
tags: [Jekyll, Markdown, atom, MD Writer]
comments: true
---

* TOC
{:toc}

# 이 글을 쓰는 이유
개인적으로 글 쓰는 도구를 위한 개발은 내 취향은 아니지만, 반복적인 작업이 너무 귀찮아서 패키지 개발(아닌 수정)을 해버렸다. 이런 발가락만 담근 경험은 쉽게 잊혀지기 쉽고, 느낌상 이번이 마지막 개발이 아닌 것 같은 느낌이 들어서 미래의 나에게 남긴다.

# 개발 환경
[Git](https://git-scm.com/), [Atom](https://atom.io/)만 설치하면 되는듯

# 결과물
[레포지토리](https://github.com/karlbishnu/md-writer)

[git commit](https://github.com/karlbishnu/md-writer/commit/d486e57442fd60d32b580b57ae7bd1af8e9b7bf3)

# Walk-through
## 개발 초기
1. [공식 블로그](https://flight-manual.atom.io/hacking-atom/sections/package-word-count/) 에서
[Package Generator](https://flight-manual.atom.io/hacking-atom/sections/package-word-count/#package-generator) - [The Flow](https://flight-manual.atom.io/hacking-atom/sections/package-word-count/#the-flow) - [Counting the Words](https://flight-manual.atom.io/hacking-atom/sections/package-word-count/#package-generator) - [Basic Debugging](https://flight-manual.atom.io/hacking-atom/sections/package-word-count/#basic-debugging) 순으로 훑어 보고 따라함.
2. [Md-Writer](https://github.com/zhuochun/md-writer) 패키지를 정상적으로 설치 (의존성 해결용)
3. [Md-Writer](https://github.com/zhuochun/md-writer) Clone
4. 내가 필요한 것은 새로운 파일을 생성할 때 파일 경로, 파일명, 그리고 초기 템플릿을 프로그램으로 쓰는 것이므로 해당 파일 찾음 (확장자가 coffee라서 당황)
5. [Coffee Script](https://coffeescript.org/)가 뭔지 [공식 홈페이지](https://coffeescript.org/)랑 [한글 블로그](https://bblog.tistory.com/299)에서 후다닥 봄

## 카테고리 추가
6. 간단하게 카테고리 입력 칸 추가 함. category로 입력 받은 값은 다음과 같이 쓰일 예정이라, 기존에 있던 Directory에 입력 받는 것보다 좋았음.
  - 포스트 루트 디렉토리 아래의 category 별 디렉토리로 포스트들 관리
  - Permalink 의 첫 경로변수
  - 초기 템플릿의 카테고리 항목에 입력
  - 태그의 첫 번째 아이템으로 자동 생성
```coffeescript
@label "Category", class: "message"
@subview "categoryEditor", new TextEditorView(mini: true)
```
7. 그리고 Directory 입력칸이 쓰인 곳과 비슷한 위치에 소스 추가함
```coffeescript
initialize: ->
    editors = [@titleEditor, @pathEditor, @categoryEditor, @dateEditor]

    ...

    @pathEditor.getModel().onDidChange => @updatePath()
    @categoryEditor.getModel().onDidChange => @updatePath()
```
8. 입력창에 값을 입력할 때마다 값이 변하는 이벤트를 감지해서 display가 되는 것을 보고 해당 함수 확인
```coffeescript
updatePath: ->
    @message.html """
    <b>Site Directory:</b> #{@getFileDir()}<br/>
    <b>Create #{@constructor.fileType} At:</b> #{@getFilePath()}
    """
```
  getFilePath()를 아래와 같이 수정
```coffeescript
getFilePath: ->
  path.join(@pathEditor.getText(), @categoryEditor.getText(), @getFileName())
```
9. 여기까지 하고 잘 카테고리의 디렉토리 생성이 잘 되는 것은 확인

## 수정 된 패키지 확인
  1. 공식적으로 배포된 패키지가 **설치되지 않아야 함**
  2. 물론 atom을 커맨드 창에서 "atom -d"로 개발자 모드로 실행시면 가능하긴 하다. ([참고 링크](https://discuss.atom.io/t/load-developing-package/2554))
  3. 그러면 매번 커맨트 창에서 실행해야하는 것이 귀찮으므로, 공식 패키지가 설치 되지 않은 상황에서 Atom이 자동으로 개발중인 패키지를 로드하도록 하자.
  ```shell
  >cd <패키지 개발 루트 디렉토리>
  >apm link
~/.atom/packages/markdown-writer -> ~/md-writer
  ```
  4. 그리고 다시 atom을 실행한 후 개발한 내용이 반영 된 것을 볼 수 있다.

# 자잘한 잡지식
1. 다른 coffeescript import는 상대경로로 가능하다.
```coffeescript
NewFileView = require "./new-file-view"
```
2. 다른 파일에서 쓸 수 있게 하는 키워드는 다음과 같다.
```coffeescript
module.exports =
class NewDraftView extends NewFileView
```
"NewDraftView 는 NewFileView 클래스를 상속받고 외부에서 쓸 수 있다." 정도로 읽으면 될 듯.
3. @가 많은데, 이는 this의 별칭
4. =>, fat arrow 는 함수가 this객체의 내부 프로퍼티에 접근가능하게 한다.
5. 플러그인 개발할 때 꼭 익힐 단축키
  - &#8984; - &#8997; - &#8963; - L : Atom 인스턴스 재시작 (플러그인 수정 후 적용 확인)
  - &#8984; - W : 현재 탭 닫기
  - &#8984; - ₩ : 멀티 인스턴스로 떠있는 Atom간에 이동. 예를 들어 플러그인 프로젝트로 열린 Atom과 Jekyll블로그 프로젝트로 열린 Atom간의 이동 (윈도우를 메인으로 쓰고 있는 나로서는 이게 맨날 헷갈린다. 윈도우는 무조건 alt-tab인데...)
  - &#8984; - S : 세이브... IntelliJ나 Pycharm에서 제공하는 오토 세이브 기능이 고마워진다.
