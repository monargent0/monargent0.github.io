---
title: 나만의 블로그 GitBlog 만들기
author: monargent0
published: true
categories: [GitBlog] 
tags: [gitblog , tutorial] # 소문자
pin: false
---

*개발 블로그를 만들어 보기로 결심하면서 첫번째로 나의 깃블로그 생성과정을 기록해보려고 한다.*

> 개발 환경 : **MacOS , M1**

---

## GitBlog 만들기  

### 1.1 GitHub에 Blog Repository 생성하기  
깃 블로그를 만들기 위해서는 내 github에 blog 저장소를 만들어야 한다.  
이런 저런 방법이 다양하게 있지만 가장 간단해 보이는 *jekyll 테마 repository를 fork 해오는 방식으로 생성했다!*  

저장소 이름은 **Git계정이름.github.io** 으로 생성한다.  
계정이름과 다르게 repo이름을 설정해서 gitname.github.id/blabla 으로 사용하는 방법도 있다고 하지만 보기에 깔끔해 보이지 않아서 패스~  
저장소 이름은 fork 해올 때 부터 바꿔서 입력하든, fork 후 변경하든지 하면 된다.  
fork한 깃블로그 repository를 로컬로 clone 해둔다.  

<blockquote class="prompt-info"><div><p>저장소의 이름은 꼭 gitusername.github.io 로 생성/변경한다!</p></div></blockquote>

### 1.2 Jekyll Theme 고르기
jeykll 테마를 모아둔 사이트에서 원하는 테마를 고르면 된다.  
"jekyll 테마 추천" 이나 "jekyll 테마 사이트"로 검색하면 다양한 테마를 찾아볼 수 있다.

검색했을때 많이 나온 사이트 두 개.
- <https://jekyllthemes.io/free>
- <http://jekyllthemes.org/>

여러가지 테마로 만들어보고 검색하면서 최종적으로 고른 테마는 [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy)이다.    
  
[Chipy 미리보기 사이트](https://chirpy.cotes.page)

### 1.3 GitBlog 저장소 기본 세팅하기  

#### 1.3.1 branch 변경하기
깃블로그가 정상적으로 만들어졌다면 자동으로 gh-pages 브렌치가 생긴다.  
Gitblog 저장소의 Settings - Pages - Build and deployment에서 Branch를 gh-pages로 변경하고 save한다. 

[GitHub Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

#### 1.3.2 gitignore 수정하기
jekyll을 사용하면 생기는 Genfile이 git에 올라가면 에러가 생길수도 있다고 한다.  
따라서 미리 Gemfile을 gitignore에 추가해두자!  
```  
Gemfile.lock   
```

#### 1.3.3 Chirpy 테마 초기화
테마를 fork하면 테마 자체에 설명을 위한 파일들도 같이 있기 때문에 초기화를 해준다.  
터미널 위치는 깃블로그 저장소
```shell
tools/init.sh
```
성공하면 Initialization successful! 멘트가 나온다

> 여기까지 과정은 깃블로그를 만든 것, 로컬에서 깃블로그를 미리 보고 싶다면 다음 과정이 필요하다. 

---

## 로컬 환경 구축하기

### 2.1 Ruby (jekyll) 설치하기 
jekyll을 사용하기 위해서는 ruby 설치가 필수이다.   
macOS에는 이미 Ruby가 깔려있으므로 생략하고 jekyll과 bundler을 설치한다.

[jekyll](https://jekyllrb.com/docs/installation/macos/)에서 설치 방법을 제공하고 있다.  
순서대로 따라하면 jekyll 설치가 끝난다!  

<blockquote class="prompt-tip"><div><p>혹시 어떤 쉘 방식을 사용하는지 모른다면 터미널에서 확인!  <code class="language-plaintext highlighter-rouge">echo $SHELL</code>
</p></div></blockquote>

### 2.2 Bundler 설치하기 
jekyll에서 제공하는 대로 설치했다면 다음 명령으로 설치하면된다.
터미널은 깃블로그 저장소로 이동
```shell
bundle
```

그 외 방법
```shell
gem install jekyll bundler
```
참고 : <https://jekyllrb.com/docs/>

### 2.3 Jekyll 로컬 서버 실행하기 
터미널에서 cd로 깃블로그 저장소로 이동 후 다음 명령을 실행한다.  
```shell
jekyll serve
# 또는
bundle exec jekyll serve
```

정상적으로 실행 되었다면 출력된 내용에 서버 주소가 있을 것이다.  
<code class="language-plaintext highlighter-rouge">Server address: http://127.0.0.1:4000/</code>  
웹 브라우저에서 위 주소로 이동하면 깃 블로그가 짜잔~ 나타난다!   
  

---

## 블로그 생성 과정 요약 

### GitBlog 생성 과정 
1. 내 GitHub에 마음에 드는 Jekyll 테마를 Fork 해온다.
2. Git 저장소 이름은 *본인Git계정이름.github.io* 로 변경한다.
3. 블로그 저장소의 Settings -> Pages -> Build and deployment의 Branch를 master에서 *gh-pages*로(/(root)) 선택 후 save버튼을 눌러 변경한다.
4. _config.yml 등 필요한 부분을 본인 계정으로 변경한다.
5. css나 구성도 원하는대로 변경하면 나만의 블로그 만들기 끝!

### Local에서 블로그 확인하기 
1. ruby, jekyll, bundler 설치한다.
2. 터미널에서 깃블로그 저장소로 이동 후 <code class="language-plaintext highlighter-rouge">jekyll serve</code> 실행
3. **127.0.0.1:4000** 에서 내 블로그를 미리보기!
4. **ctrl+C** 로 jekyll serve 종료.
    
<blockquote class="prompt-info"><div><p>guthub.io에 반영되는 시간이 길어서 바로바로 변경된 점을 확인하기 위해서는 local에서 보는것이 편하다.</p></div></blockquote>

---

### 참고 블로그
하얀눈길님 블로그 : [Jekyll Chirpy 테마 사용하여 블로그 만들기](https://www.irgroup.org/posts/jekyll-chirpy/)  
안스LAB : [Github 블로그 시작하는 방법(로컬 설치 없이 쉽게 만들기)](https://ahnslab.com/21-how-to-start-github-blog/#3-%ED%85%8C%EB%A7%88-%EC%84%A0%ED%83%9D%ED%95%98%EA%B3%A0-%EB%B3%B5%EC%82%AC%ED%95%B4%EC%98%A4%EA%B8%B0)
