# 리액트 컴포넌트

## 1.0. 컴포넌트를 왜 생성하는가?

- 프로젝트 규모에 따라 협업이 필요로 함.
- 기능별로 html, css, js 가 별도로 관리 필요.

## 1.1. 컴포넌트에 배치되는 내용

- JSX 가 배치된다. (리액트용 HTML 태그 class => className)
- css 가 배치된다. ( background: url(경로문제) )
- js 를 배치된다.

## 1.2. 이미지를 배치하는 2가지 경우(주의사항)

- 태그에 이미지를 배치한 경우
  : public/images 폴더를 참조합니다.

```html
<img src="./images/etc/logo-kakao.png" />
```

- css 배경으로 이미지를 배치한 경우
  : src/images 폴더를 참조합니다.
  : css 파일을 js 컴포넌트에서 사용하면 webpack 이 압축한다.

```css
background: url("../images/icon/icon-search.png");
```

# JS 14 장

```txt
// var : 값을 담을 공간을 마련해줘.....
  // var 이름 : 값을 담은 공간에 꼬리표를 붙여줘.
  var age = 15;
  var nickName = "hong";
  function go(){
  }
  console.log(age)
  console.log(window.age)

  모듈(기능별 파일코드)은 import/export 문법을 써서 변수 범위를 설정한다.

 class 장을 보아야 해요.

  외부에서 변수 및 함수에 접근할 수 있는 권한
  public    : 외부 어떤 곳에서도 사용할 수 있다.
  private   : 외부에서 절대로 사용할 수 없다.
  protected : 허용한 대상만 사용할 수 있다.
```
