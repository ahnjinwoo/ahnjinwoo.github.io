---
layout: post
title:  "우분투 16.04에서 Jekyll과 Github Pages 설정하기"
date:   2016-10-06 01:15:00 +0900
categories: setting jekyll
permalink: /archivers/setting-Jekyll-ubuntu16
---


# 과정 1단계

## git
일단 기본적으로 git이 필요하다.

```
sudo apt-get install git
```


## Ruby
Ruby 2.x 버전, ruby-dev가 필요하다.

```
sudo apt-get install ruby2.3 ruby2.3-dev
```


## Jekyll

지킬 박사님을 모실 시간이다.
설치 속도를 빠르게 하기 위해서, documentation은 설치에서 제외하도록 옵션을 주었다.

```
sudo gem install jekyll --no-rdoc --no-ri
```

설치가 제대로 되었는지 확인해보자.

```
jekyll -v
```


## github-pages

```
sudo apt-get install zlib1g-dev
sudo gem install github-pages --no-rdoc --no-ri
```


## bundler

```
sudo apt-get install bundler
```


## Github

### 가입에서 clone까지
1. [github.com에 회원 가입을 한다.](https://www.github.com)
2. USERNAME.github.io 라는 이름의 repository를 생성한다. 자신의 USERNAME이랑 이름을 맞춰줘야 한다.
3. 자신의 repository를 git clone한다. 이 때, Clone with SSH를 권장한다. Clone with HTTPS를 했을 경우는 나중에 push할 때 문제가 생길 수 있다.

```
git clone git@github.com:USERNAME/USERNAME.github.io.git
```


### 수정사항 반영
1. clone한 디렉토리에서 index.html 파일을 수정해본다. 간단하게 아무 말이나 적어본다.
2. git add, git commit, git push의 과정을 통해 수정 사항을 반영한다.
3. 자신의 사이트에 접속해서 방금 적은 말을 확인해본다.

```
http://USERNAME.github.io
```

초라하긴 하지만 어쨌든 내 블로그가 만들어졌다.


# 과정 2단계
이번에는 지킬을 이용해보겠다.

## 새로운 사이트 생성

```
jekyll new my-site
cd my-site
```
지킬을 이용하여 내 블로그를 체계적으로 만들었다.
이제 _config.yml을 적절하게 수정하고, _posts 디렉토리 안에 포스트를 작성하면 된다.

포스트 파일명은 YYYY-MM-DD-제목.md 형태로 해야 한다. [<b>이 페이지를 참고해서 작성하면 된다.</b>](https://jekyllrb.com/docs/posts/)

파일의 가장 상단에는 Front Matter를 작성해야 한다. [<b>이 페이지를 참고하도록 하자.</b>](http://jekyllrb.com/docs/frontmatter/)


## 사이트 빌드 및 로컬 서버 구동
기본적인 감을 익혔으면 이제 내 컴퓨터에서 로컬 서버를 돌려보자.

```
jekyll serve --watch
```
문제 없이 잘 되었으면, 콘솔에 서버 주소가 나올 것이다. 해당 주소로 접속하자.
http://127.0.0.1:4000 혹은 http://localhost:4000 따위의 주소로 들어가면 된다.


# 과정 3단계
사실 이대로는 너무 초라하다. 이제 마음에 드는 예쁜 테마를 적용할 차례다.

## 예쁜 테마 찾기
구글에서 "jekyll theme" 이라고 검색해본다.

그 중에서 [http://jekyllthemes.org](http://jekyllthemes.org)를 둘러보면 사람들이 올려 놓은 여러 테마를 구경할 수 있다. 데모를 둘러본 뒤에 마음에 드는 테마를 다운로드하거나 fork하자.


## 복사

그리고? 간단하다. 내 디렉토리에 복사해오면 된다. 대부분 MIT 라이선스일 것이다. 저작권 표시만 해주고, 마음대로 쓰면 된다.
문제 없이 동작하는지 확인하자.

```
jekyll serve --watch
```


## git push

git add, git commit, git push의 과정을 통해 수정 사항을 반영한다.
자신의 사이트에 접속해서 제대로 돌아가는지 확인하자.

```
http://USERNAME.github.io
```
사이트를 빌드하는 과정에서 뭔가 문제가 생기면 메일이 날아올 것이다.


## 트러블 슈팅

뭔가 깨진다면 다음 방법으로 해결하자.

>
1. 테마 원본을 복사해올 때 .gitignore 파일도 복사해 와야 한다. 놓치기 쉽다.
2. _config.yml 파일을 수정한다.
<br>url: 내 주소로 바꾸기
<br>baseurl: ""로 바꾸기

앞으로 테마 원본을 조금씩 수정하면서 감을 잡아나가면 된다.


## 지킬 부트스트랩
예전에는 보다 쉽고 편리한 지킬 부트스트랩이라는 것을 많이 이용했던 모양이다.

[http://jekyllbootstrap.com/](http://jekyllbootstrap.com/)

새 포스트를 작성할 때 간단한 명령어로 시간 정보가 자동으로 생성되면서 포스트가 나오니까 편리하다.
테마도 몇 개 없지만 그래도 꽤 쓸만하다.

그렇지만 메인 개발자가 손을 놓았고 더 이상 관리되지 않는다.
지킬 부트스트랩으로 블로그를 시작한다면 향후에 버전 관련 문제에 휘말리게 될 수도 있다.

그래도 공부 목적으로 뜯어본다면 꽤 괜찮을 것 같다.

