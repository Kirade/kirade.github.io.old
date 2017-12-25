---
layout: "post"
title: "[Dev] Mac OS 개발환경 세팅 - ngrok"
date: "2017-12-24 15:53"
category: Dev
tags: ngrok macOS
---

## Background
로컬 환경에서 개발중인 서버는 일반적으로 외부에서 접근할 수 있는 방법이 많지 않습니다. 로컬 서버의 내용을 보여주기 위해 외부 서버에 업로드하고 확인하는 방식을 활용하는 등의 번거로운 일이 됩니다. 디자이너 혹은 기획자들과 협업할 때, 개발중인 페이지를 보여주기 위해 이런 번거로운 작업들을 하는것은 굉장히 수고스럽기 마련입니다.

저 또한, 개인 프로젝트를 진행하며 도움을 구하고자 여러 사람들에게 개발 진행상황을 보여줘야할 순간들이 있었습니다. 한 포스팅을 보다가 우연하게 `ngrok`이라는 툴을 사용하면 이런 과정없이 간단히 로컬서버에 터널링하여 접속할 수 있다는 것을 알게 되었고 이 툴을 유용하게 사용하게 되었습니다.

---
## Study

# ngrok
>It connects to the ngrok cloud service which accepts traffic on a public address and relays that traffic through to the ngrok process running on your machine and then on to the local address you specified.

`ngrok`은 자신의 클라우드 서비스를 활용하여 공개 주소(public address)를 `ngrok`가 프로세스로 실행중인 컴퓨터로 연결시켜 명시된 로컬 서버의 주소로 연결합니다.

이런 역할을 하는 프로그램이 `ngrok`만 있는 것은 아니지만, 이런 것들에 최적화 되어있어 굉장히 활용도가 높습니다.

공식 홈페이지에서 소개하는 장점들을 소개드리면,
* Demoing web sites without deploying
  - 웹사이트를 배포하지 않고 데모를 한다
* Building webhook consumers on your dev machine
  - 자신의 개발환경으로 웹훅을 만든다
* Testing mobile apps connected to your locally running backend
  - 개발 환경 백엔드를 활용하는 모바일 앱을 테스트한다.
* Running personal cloud services from your home
  - 개인 클라우드를 집에서 사용한다.

### 설치 및 사용
[ngrok 공식 페이지](https://ngrok.com/)에서 운영체제 별로 알맞은 버전을 다운로드 할 수 있습니다.

다운로드 후, `PATH`아래에 ngrok 경로를 추가해 주면 커맨드라인에서 `ngrok`커맨드를 활용할 수 있습니다.

다음은 활용 예시 입니다. 다음 명령어를 입력하면 http 모드로 8000번 포트를 연결하는 프로세스를 실행시킵니다.
```shell
$ ngrok http 8000
```

입력하면 `ngrok`가 실행되는 현황판이 표시되고, `Forwarding`에 표시되는 주소로 자신의 로컬 서버가 포워딩 됩니다. 따라서 자신의 스마트폰 또는 인터넷으로 해당 주소에 접근하면 자신이 개발하고 있는 로컬 서버로 연결됩니다. 또한 접속 기록, 로그들이 표시됩니다.

---
## Reference
* [ngrok 공식 페이지](https://ngrok.com/)
