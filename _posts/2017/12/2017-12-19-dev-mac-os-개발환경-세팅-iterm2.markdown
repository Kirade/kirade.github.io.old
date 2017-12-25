---
layout: "post"
title: "[Dev] Mac OS 개발환경 세팅 - iterm2"
date: "2017-12-19 21:48"
category: Dev
tags: macOS iTerm2
---

## Background
macOS를 사용하면 Termianl.app 이라는 기본 터미널 앱이 설치되어 있습니다. 운영체제에 기본적으로 탑재되어있는 프롬프트 쉘 답게 대부분의 기능을 무리없이 소화합니다. 하지만, 터미널을 더 편리하게 다양한 기능을 탑재한 새로운 형태의 쉘들은 기본적으로 설치되어 있는 프로그램 보다 매력적인 부분들이 많습니다. 그 중에서 많이 알려진 iTerm2이라는 앱을 개발 환경에 설치하였고 지원하는 여러 기능들을 활용해 개발에 도움을 받고 있습니다.

---

## Study

>What is iTerm2?
iTerm2 is a replacement for Terminal and the successor to iTerm. It works on Macs with macOS 10.10 or newer. iTerm2 brings the terminal into the modern age with features you never knew you always wanted.

**iTerm2?**

iTerm2는 터미널과 iTerm을 대체하기 위한 수단으로 개발되었습니다. macOS 10.10이상의 버전에서 작동하고 사용자들의 요구에 맞춘 강력한 기능들을 제공합니다.

>Why Do I Want It?
Check out the impressive features and screenshots. If you spend a lot of time in a terminal, then you'll appreciate all the little things that add up to a lot. It is free software and you can find the source code on Github.

**왜 사용해야 하는가?**
Github에서 개발되는 오픈소스 소프트웨어이고, 터미널에서 오랜시간 개발을 진행하는 개발자들은 터미널 내 사소한 도움을 주는 기능에도 고마워 할 것이라는 생각에 착안해 만든 터미널이기 때문입니다.

>How Do I Use It?
Try the FAQ or the documentation. Got problems or ideas? Report them in the bug tracker, take it to the forum, or send me email (gnachman at gmail dot com).

**어떻게 사용하나요?**
[iTerm2 홈페이지](https://www.iterm2.com/index.html)에서 찾을 수 있는 FAQ나 공식문서를 참고하시면 됩니다.

### 특징
iTerm2는 [iTerm2 Features](https://www.iterm2.com/features.html)에서 다양한 기능들을 소개합니다. 수도없이 많은 기능이 있기 때문에, 제가 실제 활용할 때 도움이 되었던 몇 가지 기능들만 소개해 보겠습니다.

1. Split Panes  
터미널 창을 가로 혹은 세로로 다양한 방법으로 나눌 수 있습니다. 각각의 세션은 다른 세션이기 때문에 동시에 여러 작업을 한 화면에서 수행을 가능하게 하여, 여러개의 창을 동시에 이동하며 작업을 할 필요가 없게 만들어 줍니다.  

    이 후 포스팅에서 소개하는, `tmux`에서도 창을 분할하여 세션별로 사용할 수 있는 기능을 가지고 있습니다. 하지만 해당 툴의 설치 없이 iTerm2앱 자체에서 지원하는 기능 또한 강력합니다.

2. Hotkey Window  
iTerm2는 Hotkey를 제공하여 터미널 앱에서 개발할 때 다양한 활동을 핫키로 입력하거나, 혹은 심지어 활성화된 앱이 터미널이 아닌경우에서도 핫키를 적용하여 터미널 앱을 활성화 시킬 수 있습니다.

    iTerm2의 preferences -> keys에서 다양한 핫키들을 설정할 수 있습니다. 또한
    Hotkey 탭을 보면 'Show/hide all windows with a system-wide hotkey'체크 박스를 활성화 하면 해당 핫키에 따라 다른 앱이 활성화 된 상태에서도 해당 핫키를 입력하면 iTerm2앱으로 돌아올 수 있습니다.

3. Search  
마지막으로 소개드리는 강력한 특징들 중 하나는 검색기능 입니다. 여느 웹브라우저를 사용하다 `Command + F`를 이용하여 문자열을 검색하듯, iTerm2 에서도 같은 명령어로 문자열을 검색하는 검색기를 활성화 시킬 수 있습니다.

### 설치
일반적인 macOS에 설치하는 APP들과 마찬가지로 공식 홈페이지에서 다운받아 압축을 풀명 실행가능한 형태의 앱 파일이 만들어진다.
