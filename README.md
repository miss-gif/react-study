# Swiper 활용

: [Swiper](https://swiperjs.com/react)

## 1. 설치

- `npm i swiper`
- public/index.html 에 link/script 태그를 제거함.

## 2. 기본 활용

- `import { Swiper, SwiperSlide } from "swiper/react";`
- `import "swiper/css";`

## 3. 기능 추가

- `import { EffectFade, Autoplay } from "swiper/modules";;`
- `import "swiper/css/effect-fade";`
- `import "swiper/css/autoplay";`
- 옵션을 지정

```js
<Swiper
  effect={"fade"}
  autoplay={{ delay: 1000, disableOnInteraction: false }}
  modules={[EffectFade, Autoplay]}
>
  <SwiperSlide></SwiperSlide>
</Swiper>
```

## 4. 옵션은 별도로 작성하기를 권장 합니다.

```js
// Swiper 의 옵션은 별도로 변수에 담아서 관리추천
const swiperOption = {
  speed: 500,
  effect: "fade",
  autoplay: { delay: 1000, disableOnInteraction: false },
  modules: [EffectFade, Autoplay],
  onInit: (swiper) => {
    // 매개변수 swiper 는 현재 생성된 슬라이드를 말함.
    swiper.autoplay.stop();
    swLogoSlide.current = swiper;
  },
};

<Swiper {...swiperOption}></Swiper>;
```
