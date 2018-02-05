## STEP1. Hexo CLI 설치 및 블로그 생성

```
1.$npm install hexo-cli -g
2.$hexo init blog
3.$cd blog
4.$npm install
```

### STEP2. _config.yum 설정 파일 수정

- 사이트정보
```
# Site
title: myBlogName
subtitle: myBlogSubTitle
description: myBlogDescription
author: my Name
language:
timezone:
```
-github설정정보
```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type:git
  repo:https://github.com/xmfpes/xmfpes.github.io.git
  branch:master
```

### STEP3 github에 배포하기
- /blog경로에서 hexo-deploy-git패키지 설치

```
npm install hexo-deployer-git --save
```

Hexo generate 통해 정적 리소스 생성

```
$hexo generate
```

배포

```
$hexo deploy
```

아래와 같이 Generate와 Deploy를 동시에 실행 할 수도 있다.
```
$hexo deploy --generate
```

### STEP4 포스팅 및 카테고리, 태그 생성

아래의 명령어를 통해 새 글을 생성

```
hexo new 'title'
```
/source/_posts 경로에 해당 글 md파일이 생성된다.
태그와 카테고리의 적용은 아래와 같이하고, 하단부에 글을 작성하면 된다.

```
---
title: Hexo 블로그 만들기
date: 2017-09-19 14:30:46
tags: Hexo
categories: Hexo
---
```
다 하고 나면 
```
hexo deploy
```
를 하면된다.
