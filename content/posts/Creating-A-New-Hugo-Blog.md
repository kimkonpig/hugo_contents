---
title: "Creating a New Hugo Blog"
date: 2020-07-13T20:50:39+09:00
---

# Creating A New Hugo Blog

Mac OS에 hugo를 설치해 git 연동 블로그를 만들었다. 여러가지 개념을 제대로 익히지 않은 채 만들기 시작해서 설치와 제거를 여러번 반복했다. 이런 시행착오가 다시는 없길 바라며 첫 포스팅으로 **Mac OS에 hugo 블로그 만드는 과정**을 정리해보려고 한다.



## 1. Installation

Homebrew를 사용하여 hugo를 설치한다.

Homebrew가 설치되어있지 않으면 먼저 터미널에서 아래 스크립트를 실행하여 Homebrew를 설치한다. [여기](https://brew.sh/index_ko)에서 Homebrew에 대한 자세한 내용을 확인할 수 있다.

```sh
/bin/bash -c "$(curl -fsSl https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```



Homebrew가 설치되었다면 터미널에 아래 스크립트를 실행하여 hugo를 설치한다.

```sh
brew install hugo
```



hugo version 확인을 통해 설치가 잘 되었음을 확인할 수 있다.

```sh
hugo version
```



## 2. Create New Site

hugo 블로그를 위한 New Site(새로운 폴더)를 만들어야 한다. 원하는 경로로 이동하여 hugo 명령어를 통해 new site를 만든다. (아래 스크립트 실행시 'hugo'라는 이름의 site가 생성된다. 원하는 이름으로 만들면 된다.)

```sh
hugo new site hugo
```



## 3. Set theme

hugo 에서 제공하는 여러가지 테마 중에 원하는 테마를 선택하여 내가 만들 블로그에 적용할 차례. [여기](https://themes.gohugo.io/)에서 다양한 테마를 확인할 수 있다. 내가 선택한 테마는 [m10c](https://themes.gohugo.io/hugo-theme-m10c/) 이다. 

![20200713-01](/img/20200713-01.JPG)



[Download](https://github.com/vaga/hugo-theme-m10c) 버튼을 클릭해 github로 이동하여 m10c 테마 git 주소를 복사한 후, 새로 만들었던 사이트(여기선 hugo 폴더)로 이동해 git clone 명령어를 사용하여 테마를 받아온다.

```sh
cd hugo
git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
```



clone이 완료되면 /themes/hugo-theme-m10c 폴더가 생성되었는지 확인한다. 그 다음 config.toml 파일에 테마 이름을 추가해야한다. 

```sh
echo 'theme = "m10c"' >> config.tmol
```

echo 명령어로 파일을 열지 않고 한 줄 추가할 수 있고,

```sh
vi config.toml
## theme = "m10c" 추가
```

편집기로 파일을 열어 theme = "m10c" 를 작성할 수 있다.



## 4. Run Server

지금까지 한 내용들이 어떻게 반영되었는지 한 번 확인해보고 싶다면 아래 스크립트를 실행하여 먼저 서버를 구동시킨다.

```sh
hugo server -D
```

서버가 올라가면 localhost:1313 을 입력하여 내가 만든 블로그를 확인할 수 있다.

![20200713-01](/img/20200713-02.JPG)



## 5. Ready for Deploying

로컬이 아닌 username.github.io로 호스팅하기 위해서 github에 두 개의 repository를 생성한다. 컨텐츠 저장소와 최종 빌드 배포용 저장소를 만든다. 최종 빌드 저장소를 만들 때 username.github.io 형식에 맞춰 생성한다. (gitpage에서 제공하는 url 형식이기 때문이다.)

* 컨텐츠 저장소 ex) [hugo_contents](https://github.com/kimkonpig/hugo_contents)
* 최종 빌드 저장소 ex) [kimkonpig.github.io](https://github.com/kimkonpig/kimkonpig.github.io)



github에 두 개의 repository를 만든 후 remote와 submodule을 설정한다.

####5-1. remote 설정

~~~ sh
cd hugo # 초기에 생성한 new site 폴더로 이동
git init
git remote add origin git@github.com:kimkonpig/hugo_contents
~~~



#### 5-2. submodule 설정

~~~sh
git submodule add -b master git@github.com:kimkonpig/kimkonpig.github.io.git public
~~~



설정 도중 permission denied 에러가 발생하면 [이 링크](https://docs.github.com/en/github/authenticating-to-github/checking-for-existing-ssh-keys)를 따라 순서대로 처리하면 된다.



## 6. Deploy

초기에 생성한 new site 폴더(내 폴더 이름은 'hugo')에서 아래 스크립트를 실행한다.

~~~sh
# 빌드된 내용이 담긴 public 폴더를 kimkonpig.github.io 저장소에 push 하기
cd public
git add *
git commit -m "commit message"
git push origin master

# hugo 폴더를 hugo_contents 저장소에 push 하기
cd ..
git add *
git commit -m "commit message"
git push origin master
~~~



git push가 정상적으로 되었다면 username.github.io로 접속하여 최종 배포된 페이지를 확인할 수 있다.

![20200713-01](/img/20200713-03.JPG)

아직 아무것도 없다. 이 포스팅을 시작으로 하나하나 채워나가야겠다.