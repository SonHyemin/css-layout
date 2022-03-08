# 3.http://10x19.co/

## - div.number*10>{#$}

```html
div.number*10>{#$} 을 입력 하면 이렇게된다
---------------------------
    <div class="number">#1</div>
    <div class="number">#2</div>
    <div class="number">#3</div>
    <div class="number">#4</div>
    <div class="number">#5</div>
    <div class="number">#6</div>
    <div class="number">#7</div>
    <div class="number">#8</div>
    <div class="number">#9</div>
    <div class="number">#10</div>
```

$:숫자 순서 

## - &>*

```scss
body {
  background-color: $bg;
  & > * {
    background-color: white;
  }
}
```

 & > * {   } 의 의미는 body안에있는 모든 태그를 가르킨다

 ## - grid-column-start

```scss
 .menu {
    grid-column-start: -2;
  }
```

column 이 -2부터 한자리만  차지한다는 뜻

##  - uppercase

```scss
text-transform: uppercase;
```

모든 스펠링을 대문자로 바꾼다

## - cursor: pointer;

```scss
cursor: pointer;
```

마우스 커서를 포인트로 바꾼다

## - transition

```scss
.number {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: white;
    cursor: pointer;
    transition: color 0.3s linear, background-color 0.3s linear;
        &:hover {
        background-color: $bg;
        color: white;
        }
       }
      }
```

hover의 효과를  transition으로 꾸며줄수있다 (color 와 background-color 에게 효과를줌)

## - white-space

```scss
white-space: nowrap;
```

줄 바꿈 하지않는다

## - overflow

```scss
overflow: hidden;
```

콘텐츠가 너무 커서 요소의 블록 서식 맥락에 맞출 수 없을 때의 처리법을 말함, hidden은 숨기기이다

## - background-image

``` scss
background-image: url("");
background-size: cover;
background-position: center;
```

background-image를 이용해서 배경이미지를 가져온다

background-size를 이용해서 이미지의 너비 높이 다 확대하거나 축소햇거 이미지를 맞춰줌(cover)

## - *@keyframes*

```scss
 span {
    animation: scrollText 3s linear infinite forwards;
    }

   @keyframes scrollText {
  0% {
    transform: translateX(-150px);
  }
  50% {
    transform: translateX(150px);
  }
  100% {
    transform: translateX(-150px);
  }
}
```

 @keyframes으로 어떻게 span에게 애니메이션 효과를 줄건지 설정하기 

## - gap

gap에게는  따로 color를 줄수가 없다.그렇게 때문에 body의 배경색과 grid의배경색이랑 grid-gap을 잘활용해서 gap에게 색을 준 것처럼 표현할수있다 

```scss
body {
  background-color: $bg;
  display: grid;
  grid-template-columns: 1.5fr 1.9fr 1.5fr;
  grid-template-rows: 1fr 5fr 1fr;
  gap: 1px;
  & > * {
    background-color: white;
    color: $bg;
  }
```

