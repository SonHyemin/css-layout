# 2.https://paint-box.com/

## - a태그

```scss
a {
  text-decoration: none;
  color: inherit;
  @extend %minititle;
}
a{
  text-decoration: none;  
}
```

부모 요소로부터 해당 속성의 계산값을 받아 사용합니다는 뜻 부모의 컬러가 블랙이면 블랙이됨

 text-decoration: none; 는  링크의 밑줄을 없애준다 

## - &>*:not(  )

```scss
body {
  height: 100vh;
  font-family: "Caladea";
  padding-top: 70px;
  & > *:not(.footer) {
    padding: 0px 140px;
  }
}
```

body안에 있는 태그중에 footer만 빼고 padding을 준다는 뜻

## - z-index

```scss
header {
  z-index: 1;
  position: fixed;
```

position을 주면 요소끼리 겹치기 때문에 z-index로 layer를 설정해준다

## - 그라데이션과 배경이미지 같이 주기 

```scss
.hero {
  height: 100vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("");
  background-size: cover;
```

배경이미지를 넣고 바로위에 그라데이션 효과를 줄수있다 

 background-size으로 그림을 지정한 너비와 높이에 맞게 확대 축소 할수있다

## - text-align

```scss
  h3 {
    text-align: center;
  }
```

문장의 기준을 설정할수있다

## - transition

```scss
  a {
    transition: color 0.3s linear, background 0.3s linear;
    &:hover {
      background-color: black;
      color: white;
    }
  }
```

 transition으로 hover의 효과를 꾸밀수 있다

## - even / order

```scss
 .blog__post {
    background-color: $bg;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    &:nth-child(even) {
      img {
        order: 1;
      }
    }
```

.blog__post중 even(짝수) 요소에게만 img의 우선순위를 1로해서 div보다 뒤로가게 한다 (order기본값은 0이다)
