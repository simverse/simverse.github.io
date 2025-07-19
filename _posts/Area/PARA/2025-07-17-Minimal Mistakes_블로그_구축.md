---
title: "github.io에 jekyll 기반 블로그 구축 (feat, Minimal Mistakes)"
layout: category
categories: [Area,PARA]
parent: Area
comments: true
classes: wide
tags:
  - jekyll
  - Minimal Mistakes
  - 블로그
  - github.io
date: 2025-07-16 22:00:00 +0900
last_modified_at: 2025-07-16 23:00:00 +0900
sidebar:
  nav: "sidebar-category"
---

AI 시대, 쏟아져 나오는 정보와 나의 경험을 체계적으로 관리해야겠다는 필요성으로 시작한 온라인 입주과정을 정리하였습니다.

## 0. 나의 적용기

- AI를 활용하면서 그많은 지식들과 나의 경험을 체계적으로 정리하고 관리해야겠다는 필요성을 느끼게 되었습니다.
- 그 중에서 Markdown의 단순성, 편리함과 확장성에 매력을 느끼고 무료 정적 웹 서비스가 가능한 github.io을 알게되었고, 그중 jekyll과 그 중 가장 단순한 테마 Minimal Mistakes를 선정
- 처음에는 MD 파일을 올리는 목적이라 로컬에 설치도 하지 않고, 구조만 파악하여 바로 github.io에 등록하려 했으나, front end 지식이 전무하다 시피한 내게 메뉴 구조파악도 쉽지 않음
- 그래서, 가장 단순하게 시작할 수 있는  [Minimal Mistakes remote theme starter](https://github.com/mmistakes/mm-github-pages-starter/generate) 로 시작
- 구조 파악 및 몇차례 시도하다가 결국 Rudy  설치하고 Local 버전하여 시작하여, 메뉴 체계 변경하고 기존 작성된 컨텐츠 변환
- Mermaid 그래프 출력 문제는 Cursor AI  도움을 받아 Custom html / CSS 추가하여 해결
- 댓글 기능을 giscus를 적용하다 여러 문제가 발생하여 결국 Full Version 설치 후 기존 구현된 나의 컨텐츠만을 Update.
- 다른 일과 병행하긴 했지만, 계획하고 완성하기까지 1주이상 진행하면서 중간 중간 포기하고 기존 Naver나 Tistory를 사용할까도 했지만, 새로운 체계가 필요하다는 열망이 좀 더 켰던 것 같음.

## 1. 필수 프로그램 설치

### 1) Ruby 설치

- **Windows**: [RubyInstaller](https://rubyinstaller.org/)에서 최신 버전 다운로드 및 설치
- **macOS**: 터미널에서

```bash
brew install ruby
```

- **Linux**:

```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
```

### 2) Bundler 설치

> **Ruby 환경에서의 Bundler란?**
> 
> 
> **Bundler**는 Ruby 프로젝트의 Gem(라이브러리) 설치와 버전 관리를 돕는 **패키지 매니저**입니다. Python의 **`requirements.txt`**와 같은 **`Gemfile`**을 통해 일관된 환경을 구성합니다[3](https://blog.kichul.co.kr/posts/2017/03/24/using-bundle-in-ruby/)[8](https://marsboy.tistory.com/21)[1](https://velog.io/@bada308/%ED%8C%A8%ED%82%A4%EC%A7%80-%EB%A7%A4%EB%8B%88%EC%A0%80Package-Manager%EB%9E%80).
> 
> **주요 기능**
> 
> - **의존성 관리:** Gemfile의 모든 Gem을 자동 설치[3](https://blog.kichul.co.kr/posts/2017/03/24/using-bundle-in-ruby/)[8](https://marsboy.tistory.com/21).
> - **버전 충돌 방지:** 프로젝트별 지정 버전만 사용[3](https://blog.kichul.co.kr/posts/2017/03/24/using-bundle-in-ruby/).
> - **일관성 보장:** Gemfile.lock으로 동일 환경 재현[9](https://cloud.google.com/docs/buildpacks/ruby).

터미널(명령 프롬프트)에서 아래 명령 실행:

```bash
gem install bundler
```

## 2. Minimal Mistakes 블로그 코드 준비

- 이미 GitHub에 있는 블로그 저장소를 **클론**하거나,
새로 시작할 경우 Minimal Mistakes [Starter Repo](https://github.com/mmistakes/mm-github-pages-starter)에서 **fork** 후 클론:

```bash
git clone https://github.com/your-username/your-blog-repo.git
cd your-blog-repo
```

## 3. Gemfile 확인 및 수정

- 프로젝트 폴더에 `Gemfile`이 있어야 하며, 아래와 같이 되어 있는지 확인:

```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
gem "minimal-mistakes-jekyll"
```

- 또는 remote_theme을 쓸 경우:

```ruby
gem "jekyll", "~> 4.3"gem "jekyll-include-cache"
```

## 4. 의존성 설치

프로젝트 폴더에서 아래 명령 실행:

```bash
bundle install
```

- 에러가 난다면 Ruby, Bundler, Gemfile 내용을 다시 확인하세요.

## 5. 로컬 서버 실행

아래 명령어로 Jekyll 서버를 시작하세요:

```bash
bundle exec jekyll serve
```

- 또는 라이브 리로드까지 원하면:

```bash
bundle exec jekyll serve --livereload
```

- 성공적으로 실행되면

```
Server address: http://127.0.0.1:4000/
```

메시지가 뜨고, 브라우저에서 `http://localhost:4000` 접속하면 바로 사이트가 보입니다.

## 6. 자주 발생하는 문제 해결

| 증상 | 해결 방법 |
| --- | --- |
| `bundle install` 오류 | Ruby, Bundler, Gemfile 버전 확인 |
| `jekyll serve` 오류 | Gemfile의 플러그인 누락, `_config.yml` 문법 오류 |
| 한글 깨짐 | `_config.yml`에 `encoding: utf-8` 추가 |
| remote_theme 작동 안함 | 인터넷 연결, Gemfile 플러그인 확인 |

## 

## 참고

- Jekyll 공식: [Jekyll Docs](https://jekyllrb.com/docs/)
- 공식 가이드: [Minimal Mistakes Docs](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
- 간편스타트 :  [Minimal Mistakes remote theme starter](https://github.com/mmistakes/mm-github-pages-starter/generate)