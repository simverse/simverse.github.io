---
title: "jekyll 기반 블로그에 댓글 기능 적용하기"
layout: category
permalink: /categories/Area/PARA/
taxonomy: PARA
parent: Area
tags:
  - PARA  
  - jekyll
  - Minimal Mistakes
  - comment
  - Giscus
  - GitHub Discussions
classes: wide
date: 2025-07-17 22:00:00 +0900
last_modified_at: 2025-07-17 23:00:00 +0900
comments : true
---

**Jekyll(Minimal Mistakes) 블로그에서 포스팅된 글에 댓글(Comment)을 관리하는 가장 간단한 방법**을 안내드리겠습니다.

---

## 1. 가장 간단한 방법: **Giscus**(깃허브 Discussions 기반 댓글)

- **Giscus**는 GitHub Discussions를 기반으로 하는 무료 댓글 시스템입니다.
- 별도의 서버나 복잡한 설정 없이,  
  **GitHub 계정만 있으면 바로 사용**할 수 있습니다.
- Minimal Mistakes 테마도 공식 지원합니다.

---

### **A. Giscus 세팅 방법**

### 1) 준비사항
GitHub 저장소: 블로그 소스가 올라간 저장소(예: simverse/simverse.github.io)
GitHub Discussions 활성화:
저장소의 Settings → Features → Discussions 체크(활성화)
![체크화면](/assets/images/Area/PARA/check_discusions.png)

#### 2) Giscus 설치 및 연동
- [https://giscus.app/ko](https://giscus.app/ko) 접속
- 자신의 GitHub 저장소(예: `simverse/simverse.github.io`) 선택
![giscus설치화면](/assets/images/Area/PARA/install-giscus.png)
![giscus설치완료](/assets/images/Area/PARA/confirm-install-giscus.png)
- github > setting > General > Featuer > Setup Discusions
![Set up](/assets/images/Area/PARA/setup-discusions.png)


#### 3) Giscus 설정 마무리
- 다시 giscus 페이지로 이동
![Set up](/assets/images/Area/PARA/setup-giscus.png)
- 언어 선택 : 한국어
- 페이지 <-> Discusionis 연결 : "Discussion 제목이 페이지 경로 포함" 제일 무난
- Discussion 카테고리 : 별도 목적이 없다면 "General" 선택
- 테마 : GitHub Light




- **설정 코드**(YAML 또는 HTML)와 필요한 값(repo, repo_id, category, category_id 등)을 복사

#### 3) `_config.yml`에 Giscus 설정 추가

```yaml
comments:
  provider: "giscus"
  giscus:
    repo: "simverse/simverse.github.io"
    repo_id: "복사한 repo_id"
    category: "General"
    category_id: "복사한 category_id"
    mapping: "pathname"
    reactions_enabled: "1"
    theme: "light"
```
- 위 값들은 giscus.app에서 복사한 값으로 채워주세요.

#### 4) 각 포스트의 Front Matter에 `comments: true` 추가  
(이미 defaults에 있으면 생략 가능)


#### 5) giscus 댓글 기능은 Local 실행시 안나오며, github.io에 올린 버전만 정상 동작됨. 
로컬버전
![로컬버전](/assets/images/Area/PARA/giscus_local.png)





---

### **B. 장점**

- **무료, 광고 없음, GitHub 계정만 있으면 누구나 사용 가능**
- 댓글이 GitHub Discussions에 저장되어 관리가 편리함
- 스팸 방지, 알림, 마크다운 지원 등 다양한 기능

---

### **C. 참고**

- 방문자도 **GitHub 계정**이 있어야 댓글 작성 가능(읽기는 누구나 가능)
- 기존 Disqus, Utterances 등보다 설정이 훨씬 간단

---

## 2. 요약

- **Giscus**가 가장 쉽고, 무료이며, Minimal Mistakes에서 공식 지원
- giscus.app에서 설정값 복사 → `_config.yml`에 붙여넣기만 하면 끝

---
