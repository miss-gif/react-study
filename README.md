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

## 1.3. js를 React 로 마이그레이션 진행

### 1.3.1. load 가 useEffect 로 변경

```js
window.addEventListener("load", function () {});

useEffect(() => {
  return () => {};
}, []);
```

### 1.3.2. querySelector 가 useRef(null) 로 변경

```js
const tag = document.querySelector(".bt");

const tag = useRef(null);

useEffect(() => {
  // tag.current 로 접근
  return () => {};
}, []);

<div ref={tag}> </div>;
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

# JS 15장

```txt
 var 는 없다 생각해요.
 변수 를 만들때 고민이 생겨요.

 const 변수이름  :  값을 고정시키겠다.
 let 변수이름    : 값이 수시로 바뀌어집니다.

const 사용하실 때 오해의 소지가 있는 경우

 정군은 const 는 절대로 값이 안변한다.
 값을 변경하려고 하면 에러난다.
 const age = 15;
 age = 100; // 에러.. conatant value...


 const 객체 = {}   오해의 소지가 발생합니다.

 const 정군 = {} // 이미 주소는 고정이 되어 버렸다.
 정군 = "안녕"   //  주소를 교체 하려고 했다. 그래서 const 에 위배된다. 에러

 // 주소를 교체하는 것이 아니고, 안쪽의 연결된 내용을 수정한다.

 정군.age = 100;
 정군["nicName"] = "hong guil dong";
```

# 실 업무에서 알아야 하는 상식

- nvm (Node Version Manger) 설치 및 활용
  : https://github.com/coreybutler/nvm-windows/releases
  : 설치 버전 확인 `nvm -v`
  : 설치 가능한 버전 목록 `nvm list available`
  : 설치 하기 `nvm install 버전`
  : 현재 사용중인 Node 버전 확인하기 `node -v`
  : 현재 설치된 Node 목록 확인 `nvm ls`
  : 사용할 Node 버전 선택하기 `nvm use 버전`
  : Node 설치된 경로 알아보괴 `which node`

- npm 보다는 yarn 선호
  : Node Package Manager (node_modules)
  : package.json 의 dependencies 목록을 참조
  : npm 이 가끔 다운로드 중 오류가 발생하고, 소스가 깨짐 현상
  : 예) 네이버 Toast UI 등.
  : npm 보다 안정적인 package 관리를 위해서 yarn 을 활용.
  : `npm install -g yarn`
  : `yarn --version`

- favicon 만들기(디자이너 담당)
  : https://realfavicongenerator.net/

- ::before, ::after 샘플
  : css 로 내용만들기

```html
<body>
  <style>
    .wrap {
      position: relative;
      width: 100%;
      height: 400px;
      background: goldenrod;
      margin: 100px auto;
      padding: 50px;
    }
    .box {
      width: 100px;
      height: 100px;
      margin: 100px auto;
      background: hotpink;
      text-align: center;
    }
    .box span::before {
      display: inline-block;
      content: "";
      width: 10px;
      height: 10px;
      background-color: red;
    }
    .box span::after {
      display: inline-block;
      content: "";
      width: 10px;
      height: 10px;
      background-color: blue;
    }
  </style>
  <div class="wrap">
    <div class="box">
      <span>안녕</span>
    </div>
  </div>
</body>
```

# JS 16 장

```txt
 16장. Property Attribute ( get, set, 불변객체(freeze))

 [[단어]]

 const Obj = {}
 Obj.[[Prototype]] 이렇게 정의는 되어도
                  우리는 사용할 수 없어요.
 Obj.__proto__   이렇게 접근이 가능하도록 개방됨.


 const Person = {
   age: 10
 }
 Pesong.nickName = "홍길동";

 console.log(Person.age); // 개발자가 활용
 console.log(Person.nickName); // 개발자가 활용

 Person.age //  [[value]] ===> true,

 Person.job = "학생";
 Person.age //  [[writable]] ===> true,

 // 반복을 통해서 요소들을 출력할 수있다.
 Person.age //  [[enumarable]] ===> true,

 Person.age = 10000
 Person.age //  [[configurable]] ===> true,


 const [age, setAge] = useState(0)


 const who = {} // const 적용시 불안정하다.
 who = "안녕" // 변경 불가

 who.age = 100; // 막을 방법이 없다.

 객체 변경     금지... (완벽하게 막을 수 없어서)
 : 객체를 복사해서 사용
 : lodash 라이브러리 활용 (https://lodash.com/docs/#cloneDeep)


 객체 만드는 법
 : 객체 리터럴     {}
 : 함수로 객체만드는 법 (4가지)
```

# React useState 정리

```txt

 모든 hook 들은 컴포넌트 js 의 첫번째 영역에 배치를 하자!

 hook ?

 일반 변수는 값이 바뀌어도 재렌더링 없음
 리액트 변수는 값이 바뀌면 재 렌더링 되므로 화면 반영


  1. 리액트용 변수 즉, useState 는 재 렌더링시 표현된다.

  2. 리액트용 변수 즉, useState 는 컴포넌트에서만 작성할 수 있습니다.

  3. useState 는 비동기이므로 즉시 참조할 수 가 없다.

  4. useState 에 직접 값을 변경할 수 없다.
     const [age, setAge] = useState(0);
     age = 100; (X)

  5. useState 에서 현재값을 참조하고
     즉시 갱신을 하려면 함수를 활용하여 업데이트 한다.

     const [age, setAge] = useState(0);
     setAge(age++); // 1 이 되지 않는다. 즉, 즉시 갱신 되지 않는다.
     console.log(age);
     // 우리는 1증가한 값을 기대하였다. 하지만 값은 옛날거 유지
     // 함수가 종료되면 그때 업데이트 된다.


       const [isOpen, setIsOpen] = useState(false);

       const clickMbbt = () => {

         const now = !isOpen;
         setIsOpen(now);

         //     즉시 갱신을 하려면 함수를 활용하여 업데이트 한다.

         // setIsOpen((prev) => {
         //   return !prev;
         // });

       };


   6. useState 에서 기존 값 참조 후
      직접 값 갱신 리턴 받아서 바로 사용하고 싶다.

     const [age, setAge] = useState(0);
     setAge(age++) ; // 기존 방식 (새로운 값 안나옴)

     setAge( 이전값 => { return 새로운값 }  ) // 함수 방식(새로운 값 나옴)
     setAge( prev => { return prev+1 }  ) // 함수 방식(새로운 값 나옴)
```

# JS 17 장

```txt
 1. 객체 가 뭘까?

   : 객체를 만든다는 말은 데이터를 설계하는 것.
   : 예) 유아제품을 판매하는 서비스에서 제품을 표현한다면?

   : 여러 개의 데이터와 여러 개의 기능을 묶어서
     마치 데이터종류처럼 사용할 수 있다는 장점

   하나의 이름으로  {
      데이터... 가지고 있고,
      데이터... 가지고 있고,
      데이터... 가지고 있고,
      기능...   가지고 있고,
      기능...   가지고 있고,
    }


    const Person = {
       age: 10,
       nickName: "홍길동"
    }

    Person 의 데이터 타입(종류)
    -  객체:Person ====> { age:number, nickName:string}

2. 객체 는 정말 좋은데 (다양한 자료를 묶어서 이름 한개로 표현 가능)
   만드는 방법이 2가지 형태(리터럴, 함수)를 띈다.

   2.1. 객체 리터럴 (장점: 가독성, 관리 손이 고생,  단점: CRUD)
        const Obj = { name: "귀마개", count:10}
        const Good_1 = { name: "귀마개", count:10, descript:"df"}
        const Good_2 = { name: "귀마개", count:10, descript:"df"}
        const Good_3 = { name: "귀마개", count:10, descript:"df"}
        const Good_4 = { name: "귀마개", count:10, descript:"df"}
        const Good_5 = { name: "귀마개", count:10, descript:"df"}
        const Good_6 = { name: "귀마개", count:10, descript:"df"}
        const Good_7 = { name: "귀마개", count:10, descript:"df"}
        const Good_8 = { name: "귀마개", count:10, descript:"df"}
        const Good_9 = { name: "귀마개", count:10, descript:"df"}
        const Good_10 = { name: "귀마개", count:10, descript:"df"}

   2.2. 객체 생성자(constructor) 함수 (Object) 사용


     Object() : ? 함수 call 하는 구나.

     new Object()
      : new 함수 call 하는 구나.
      : new는 문법 Object() 객체 생성

     2.2.1. 관례
      : 개발자가 함수의 모양만 봐도 객체생성함수/ 일반함수 인지 구별이 가능하다.

       Swiper()
       Axios()

      : 일반적으로 call 하는게 아니다를 표현한다면
        new Swiper()
        new Axios()

    2.2.2.  함수 안쪽에 this 는 죄송하게도 call 방식에 따라서 this 의 값은 다르다.

      function Foo() {
         //this
         goto: function () {
                this
                }
      }

      Foo(); // this 는 window

      new Foo(); // this 는 만들어질 객체 (인스턴스 : 앞으로 보관될 것)

      const go = new Food()
      go.goto(); // 여기서 this는     . 앞에 것 즉, go 를 가르킵니다.

  2.2.3. 제발 용도를 구분하셔서 함수 call 과   new 객체생성자함수 를 구분하셔서
         리턴을 하셔야 해요.

      :  일반 함수는 자유롭게 return  값;
      :  객체생성용 함수는 제발 return 적지 마세요.

  2.2.4 constructor 함수 / none-constructor 함수

      : 모든 함수 형태는 어디에 작성을 하든 new 사용가능 (constructor)

      : 근데, ES6 도입 후 new 사용못하는 함수
        (화살표함수, 축약메소드 함수 none-constructor)

  2.2.5.  new로 생성된 객체(인스턴스)의 원본확인 연산자 instanceof



   2.3. 클래스 함수 사용 (25장에서 등장)
```

# 리액트 useState 정리

```txt

  1. 매개변수이름 은 관례상 props 라고 작성합니다.

   const MbHeader = (props) => {
      return ( .....)
   }

   <Header clickMbbt={clickMbbt} age={10} ></Header>

   참조법 1.
   const MbHeader = (props) => {

      // 참조가능 : 함수이구나
      props.clickMbbt()

      // 참조가능 : 숫자구나
      props.age;

      return ( .....)
   }

   참조법 2.
   const MbHeader = (props) => {

      // 참조가능 : 함수이구나
      const clickMbbt = props.clickMbbt;
      clickMbbt();

      // 참조가능 : 숫자구나
      const age = props.age;
      age;

      return ( .....)
   }

   참조법 3.
   const MbHeader = ({clickMbbt, age}) => {

      // 참조가능 : 함수이구나
      clickMbbt();
      // 참조가능 : 숫자구나
      age;

      return ( .....)
   }

  2. 리액트 용 변수 즉, useState 이해

  :  컴포넌트에 새로고침을 진행하도록 한다. ( useEffect 를 강제 실행 )

  :  useEffect 용도?
     - 컴포넌트가 생성될 때 실행하고 싶은 것

       useEfeect( () => {

          // 죽어도 한번만 실행하라!

       }, []);   // [] 에 아무것도 작성하지 않는다면.


     - 컴포넌트가 제거될 때 실행하고 싶은 것

       useEfeect( () => {

         return () => {
             // 죽을 때 한번만 실행한다.
         }

       }, []);

     - 컴포넌트가 업데이트될 때 실행하고 싶은 것

       useEfeect( () => {

       }, [ 리액트변수 ]); // 작성을 해주면 해당 상태가 내용이 바뀌면 화면 고침

  : 리액트 변수 만들기

    const [get이름, set이름] = useState(초기값);
    const [mbMenuOpen, setMbMenuOpen] = useState(false);

  : 리액트 변수 값 고치기

   - 이러시면 안되요.

     get이름 = 값을 직접 입력은 반영안됨.
     mbMenuOpen = true;  // 이러시면 반영안되요.

   - 함수가 종료되어야 업데이트 된 결과를 참조할 수가 있다.

   - 방식은 2가지
     set이름(새로운 값);

     set이름( (현재값) => {
                      return 새로운값;
                      }
            );

    - 예제 1)
    const clickMbbt = () => {
      setMbMenuOpen(새로운값);
    };

    - 예제 2)
    const clickMbbt = () => {
      setMbMenuOpen( (기존값) => { return 새로운값 } );
    };

    - 활용 예)
   const clickMbbt = () => {

    setMbMenuOpen((prev) => {
      return !prev;
    });

   };
```
