---
title: Contributing
tags: 
 - jekyll
 - github
description: 포스팅 전 참고사항들입니다✨
---

# 포스팅 할 때 읽어주세요😎

* [포스팅 방법](#포스팅방법)
* [개발 세팅](#개발세팅)

## 포스팅방법

### 포스트 작성

`_posts` 파일 내에 양식 따라 작성하기!

### 기술 작성

`_docs` 폴더 안에 양식 따라 작성하기

`_data` 폴더 안에 `toc.yml` 수정

### 버튼 사용법

`.btn-<tag>`

```html
<button class="btn btn-success">.btn-success</button>
```

<button class="btn btn-success">.btn-success</button>
<button class="btn btn-info">.btn-info</button>
<button class="btn btn-secondary">.btn-secondary</button>
<button class="btn btn-primary">.btn-primary</button>
<button class="btn btn-danger">.btn-danger</button>
<button class="btn btn-warning">.btn-warning</button>

### 뱃지 사용법

```yaml
---
title:  "Two Thousand Nineteen"
date:   2019-06-28 18:52:21
categories: jekyll update
badges:
 - type: warning
   tag: warning-badge
 - type: danger
   tag: danger-badge
---
```

<span class="badge badge-warning">warning-badge</span>
<span class="badge badge-danger">danger-badge</span>
<span class="badge badge-success">success-badge</span>
<span class="badge badge-info">info-badge</span>
<span class="badge badge-secondary">secondary-badge</span>
<span class="badge badge-primary">primary-badge</span>

### 알럿 사용법

{% include alert.html type="info" title="알럿이란?" content="중요한 정보를 나타낼 때 사용해요!" %}

```
{%raw%}{% include alert.html type="info" title="알럿이란?" %}{%endraw%}
```

{% include alert.html type="warning" content="This is a warning" %}
{% include alert.html type="danger" content="This alerts danger!" %}
{% include alert.html type="success" content="This alerts success" %}
{% include alert.html type="info" content="This is useful information." %}
{% include alert.html type="primary" content="This is a primary alert" %}
{% include alert.html type="secondary" content="This is a secondary alert" %}

### 인용문 사용법

```
> 예시입니다.
```

> 예시입니다.

## 개발세팅
### 루비, 지킬 설치하기

```bash
$ brew install ruby
$ gem install jekyll
$ gem install bundler
$ bundle install
```

```
gem install jekyll
gem install github-pages
gem install jekyll-sass-converter
```

### 실행하기

```bash
jekyll serve
# or
bundle exec jekyll serve
```
