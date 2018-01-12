---
layout: "post"
title: "[CS] Travis CI란 무엇일까?"
date: "2018-01-12 11:20"
category: "Computer Science"
tags: TravisCI CI Github
---

## Background
저는 개인적으로 Github에 개인 프로젝트 혹은 블로그를 올려두고 사용하고 있습니다. 다양한 오픈소스들이 github에 공개되어 개발되고 있습니다. 여러 오픈소스들을 찾아보던 중 여러 오픈소스들이  내용을 소개하는 `readme.md`에
[![Build Status](https://travis-ci.org/Kirade/django_tangerine.svg?branch=master)](https://travis-ci.org/Kirade/django_tangerine) 뱃지를 가지고 있는것을 보게되었고, 이는 Travis CI에서 제공하는 빌드테스트임을 알게 되었습니다. 그래서 직접 사용해 보고자 개인 프로젝트에 적용해 보았습니다.

---

## Study
Travis CI는 Travis에서 만든 CI(Continuous Integeration)툴, 즉 지속적인 통합을 위한 툴입니다. 영어를 한글로 바로 번역하면 뜻은 이해가 되지만 잘 와닿지는 않습니다. 조금 더 풀어서 해석해보면, 해당 소스가 지속적으로 잘 작동하는지 테스트하는 것을 말합니다.

Travis CI는 github에 커밋이 될 때마다, 사용자가 따로 빌드 테스트를 실행시키지 않아도 자동으로 테스팅을 수행하고 결과를 알려줍니다.

Travis CI의 웹 사이트에서 github 계정으로 연동해 가입하면, 자신의 github에 있는 저장소들 중 관리하고 싶은 것을 선택하여 자동화 테스트를 수행할 수 있다.

### .travis.yml
Travis CI에 등록한 저장소에 루트에 `.travis.yml`이라는 설정 파일을 넣어두면, 해당 설정에 정의되어 있는 방식대로 빌드테스트를 수행하게됩니다. 다양한 언어별로, 그리고 프레임워크별로 설정의 내용이 상이할 수 있기 때문에, 구글검색 혹은 [Travis CI Docs](https://docs.travis-ci.com/)를 참고하여 설정해야 합니다.

### Build
저장소를 Travis 에서 추적하도록 등록하였고, `.travis.yml`을 작성하였다면, `git push`명령어를 실행하여 github에 올렸을 때, 자동으로 Travis는 빌드 테스트를 수행합니다.

### Badge
`readme.md`에 멋지게 올라가있는 뱃지를 받기위해서는 Travis CI페이지에서 보여주고싶은 저장소의 설정으로 이동하여 상단에 보여지는 뱃지를 클릭합니다.

클릭하면 여러종류의 스크립트를 선택할 수 있는데, 필요한 문법 형식을 선택하여 아래의 스크립트를 복사하여 붙여넣으면 보입니다. `readme.md`는 마크다운 형식입니다. 이것을 붙여넣게되면 다음과같이 뱃지가 생성됩니다.

[![Build Status](https://travis-ci.org/Kirade/django_tangerine.svg?branch=master)](https://travis-ci.org/Kirade/django_tangerine)

---

## Reference
* [Travis CI Docs](https://docs.travis-ci.com/)
* [Travis CI - hatemogi님 블로그](http://hatemogi.com/holiday-project-day-17/)
* [Django, Travis CI - Medium](https://medium.com/@erika_dike/connecting-your-django-app-to-travis-and-coveralls-c73a1a56eb06)
