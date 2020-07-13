---
title: "Adding Disqus Plug In"
date: 2020-07-13T23:35:15+09:00
---

# <!--Adding Disqus Plug-in-->

어느정도 블로그 셋팅을 마무리하고 보니 어딘가 허전함이 느껴졌다.

자고로 블로그라 하면 __소통__ 기능이 필요하지 않겠는가?

[Disqus](https://disqus.com/)에서 제공하는 플러그인을 사용해 댓글 기능을 추가해보았다.



---



## 1. 회원가입

먼저 [disqus.com](https://disqus.com/) 에 회원가입을 한다. 페이스북, 트위터, 구글 소셜 가입/로그인도 가능하다.



## 2. 등록하기

![get started](/img/20200713-04.JPG)

메인 화면에서 GET STARTED 버튼을 클릭한다.



![choose install](/img/20200713-05.JPG)

다음 화면에서 두번째 선택지(I want to install Disqus on my site)를 클릭한다. 



![info](/img/20200713-06.JPG)

필요한 정보를 입력하고 Create Site 버튼 클릭한다.

Website Name은 shortname 으로 사용할 원하는 이름을 적으면 된다. 나는 kimkonpig으로 입력했다.

Category는 자신의 블로그 카테고리를 선택하면 된다. 기술블로그라면 Tech로 선택하면 되겠지?



![step](/img/20200713-07.JPG)

3단계 과정을 순서대로 따라가면 된다.

2번 Select Platform에서 사용중인 플랫폼이 없다면

하단에 *I don't see my platform listed, install manually with Universal Code* 를 선택하면 된다.

선택 후 다음 페이지 하단에 *Configure* 를 클릭해 3번 과정으로 넘어간다.



![step3](/img/20200713-08.JPG)

등록 마지막 단계에서는 웹사이트 URL(ex. kimkonpig.github.io), 플러그인 색상 등을 선택할 수 있다.

필요한 정보를 입력한 후 오른쪽 하단에 *complete Setup*을 클릭한다.



## 3. config.toml 수정하기

![config.toml](/img/20200713-09.JPG)

등록 단계에서 지정한 shortname을 config.toml 파일에 추가해야 플러그인 설치가 끝난다.

```sh
disqusShortname = "kimkonpig" # 지정한 shortname 입력
```



## 4. 배포 후 확인

![deploy](/img/20200713-10.JPG)

git push로 deploy한 후에 본인 사이트에 접속하면 포스팅마다 개별 적용된 댓글창을 확인할 수 있다.

localhost:1313 에서는 적용되지 않는다.



![profile](/img/20200713-11.JPG)

등록된 댓글들은 [disqus](https://disqus.com/)에 로그인 후 profile에서 확인할 수 있다.

이런 기능을 손쉽게 뚝딱 추가할 수 있다니 신기하다. 공부할 게 점점 더 많아진다.