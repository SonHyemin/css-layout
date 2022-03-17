# 6. https://tolv.dk/ 

메뉴 상단에 고정하기

```scss
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 50px;
}
```

- fixed

바로 밑에 자식을 선택할때

```scss
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 50px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  align-items: center;
  h1 {
    place-self: center center;
  }
  > span {
    justify-self: end;
  }
```

-  의미는 >  header 안에 있는 자식인 span 이라는 뜻 

하나만 빼고 적용시킬때

```scss
 ul {
      display: flex;
      li:not(:last-child) {
        margin-right: 10px;
      }
    }
```

- li의 마지막 자식만빼고 적용한다는 뜻

hover 에게 효과 시간주기

```scss
 transition: all 0.2s linear;
```

필터로 블러처리하기

```scss
 &:filter: blur(50px);
```







 grid-template-rows: calc(100vh - 60px);









