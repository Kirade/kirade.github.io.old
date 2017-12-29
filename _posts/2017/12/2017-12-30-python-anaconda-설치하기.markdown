---
layout: "post"
title: "[Python] Anaconda 설치하기"
date: "2017-12-30 00:04"
category: Python
tags: Anaconda Python
---

## Background
무료로 수강가능 한 머신러닝 기초 강의를 좋은기회에 온라인으로 수강하게 되었습니다. 처음 강의는 개발 환경 설정을 위한 `Anaconda`를 설치하는 내용이었습니다. 강의 내용그대로 설치가 정확하게 일치하게 진행되지 않아 이곳 저곳 찾아보면서 설치를 완료했습니다. 강의 내용대로 공식 홈페이지에서 설치하는 방법이 아닌 `pyenv`패키지를 이용하여 설치하는 과정을 소개합니다.

## Study
>With over 4.5 million users, the open source Anaconda Distribution is the easiest way to do Python data science and machine learning. It includes the conda package and virtual environment manager which ensures you can quickly and easily install and run complex data science and machine learning environments like Scikit-Learn and Tensorflow with just one "conda install" command.

공식 홈페이지에 소개되어 있듯이, 아나콘다는 데이터 사이언스와 머신러닝을 위한 패키지들을 종합적으로 가지고 가상환경들까지 관리할 수 있도록 기능을 하는 유용한 툴입니다. 파이썬을 이용해서 데이터 사이언스 혹은 머신러닝을 공부한다면 필수적으로 설치해야 되는 프로그램 중 하나일 것입니다.

인프런 초급 머신러닝 강의에서 설치를 진행할 때, 공식 홈페이지를 통해 진행하였는데 받은 인스톨러를 통해 설치하면 로컬에 파일이 설치되고 사용하고 있는 zsh이 아닌 bash쉘에 PATH로 등록이 기본적으로 되었습니다. 저는 파이썬 개발 환경을 `pyenv`를 통해 버전은 물론 가상환경 까지 전체적으로 관리하고 있습니다. 다행히도 `pyenv`에서 `anaconda`를 설치 할 수 있도록 기능을 제공하여 이를 통해 설치를 진행하였습니다.

## 설치

pyenv가 설치되어 있지 않다면 brew 를 활용하여 pyenv 를 설치합니다.

```shell
$ brew install pyenv
$ brew install pyenv-virtualenv
```

설치가 완료되었다면 다음 명령어로 설치가능한 파이썬 버전은 물론 아나콘다 버전들의 목록을 볼 수 있습니다.

```shell
$ pyenv install -l
```

아나콘다를 설치하기 위해 원하는 아나콘다의 버전을 확인한 뒤, 다음과 같이 입력합니다.
> python2 버전과 python3 버전이 서로 다르기 때문에 주의하여 설치하셔야 합니다. `anaconda2`는 python2, `anaconda3`는 python3 버전을 지원합니다.

```shell
$ pyenv install anaconda3-5.0.0
```
많은 패키지를 설치하기 때문에, 시간은 오래 걸릴 수 있습니다. 설치가 완료되었다면 `pyenv`의 다음 명령어를 활용하여 확인합니다.

```shell
$ pyenv versions
```
여러 버전 목록들 중 anaconda3-5.0.0이 설치된 것을 알 수 있습니다. 이후 아나콘다를 활용하기 위해 해당 버전으로 이동하여 사용하거나 virtual environment를 새로 생성하여 사용가능합니다.

해당 버전으로 이동하여, 설치된 패키지를 확인합니다.
```shell
$ pyenv shell anaconda3-5.0.0
$ pip list
```

## Reference
* [아나콘다 공식 페이지](https://www.anaconda.com/what-is-anaconda/)
* [인프런 - 머신러닝](https://www.inflearn.com/course-status-2/)
