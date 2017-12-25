---
layout: "post"
title: "[Dev] Mac OS 개발환경 세팅 - tmux"
date: "2017-12-23 20:50"
category: Dev
tags: macOS tmux
---

## Background
개발을 진행할 때에 터미널을 사용하다보면, 여러 터미널 창을 키고 필요할 때마다 각 창을 활성화 시켜서 작업을 진행하곤 했었습니다. `tmux`는 그런 불편함을 줄이기 위해 저의 개발환경에 적용한 유용한 도구입니다.

---
## Study
>tmux is a "terminal multiplexer", it enables a number of terminals (or windows) to be accessed and controlled from a single terminal. tmux is intended to be a simple, modern, BSD-licensed alternative to programs such as GNU screen.

### Tmux?

`tmux`는 단일 터미널에서 여러개의 터미널 (혹은 윈도우)를 만들어 사용할 수 있도록 해주는 '터미널 멀티플랙서' 입니다.

의존성을 가지고 있는 라이브러리는 `libevent`와 `ncurses`입니다. 간단히 설명드리자면

* `libevent`
> The libevent API provides a mechanism to execute a callback function when a specific event occurs on a file descriptor or after a timeout has been reached. Furthermore, libevent also support callbacks due to signals or regular timeouts.

`libevent`는 파일 디스크립터에 특정 이벤트가 일어나거나 타임아웃이 만료되었을때 발생하는 콜백함수를 작동시키는 API를 제공 합니다. 또한 시그널이나 규칙적인 타임아웃으로 만들어지는 콜백 함수들 또한 지원합니다.

* `ncurses`

>ncurses (new curses) is a programming library providing an application programming interface (API) that allows the programmer to write text-based user interfaces in a terminal-independent manner. It is a toolkit for developing "GUI-like" application software that runs under a terminal emulator. It also optimizes screen changes, in order to reduce the latency experienced when using remote shells.

`ncurses`는 프로그래머가 터미널 독립적인 텍스트 기반의 인터페이스를 만들 때, 도움이되는 API를 제공합니다.

### 설치

`Homebrew`를 사용하는 macOS라면 다음 명령어로 간단하게 tmux를 설치할 수 있습니다.
```shell
$ brew install tmux
```

### 기능

`tmux`를 사용하기 위해서는 여러 가지 방법이 있습니다.
```shell
# 세션 만들기
$ tmux

# 이름을 가진 새로운 세션 만들기
$ tmux new -s `세션 이름`
```

또한, `tmux`가 실행된 뒤, 세션 내에서 명령어를 실행하기 위해서는 `control + b`를 입력하여 모든 명령을 시작하곤 합니다.

유용하게 사용되는 명령어 몇 가지를 알아보겠습니다.
```shell
# 새 윈도우 만들기
$ control + b, c   

# 윈도우 종료
$ control + b, d

# pane 가로 분할
control + b, "

# pane 세로 분할
control + b, %
```

이 이외에도 tmux에는 굉장히 많은 명령어가 있습니다.
* [tmux document](http://man.openbsd.org/OpenBSD-current/man1/tmux.1)
* [tmux 관련 블로그](http://www.haruair.com/blog/2124)
---
## Reference
* [tmux - github](https://github.com/tmux/tmux/wiki)
* [libevent](http://libevent.org/)
* [ncurses](http://www.gnu.org/software/ncurses/ncurses.html)
