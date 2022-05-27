# css layout

scss 하기 위해서는 node.js 설치하기

## flex box

- disply:block 는 box 속성을 가짐, 그래서 옆에 아무도 올수 없고 세로로 나열함   ex) div
- disply:inline-block는 box 속성을 가짐, 그래서 block속성을 유지할수있게 해주고 가로로 나열함  (withd,height 적용 가능)
- **inline-block** 와 **inline** 차이점: inline은 box가 아니다 그래서 너비와 높이가 적용이 안된다(두요소는 children에게적용해야함)
- css만으로 디자인을 디스플레이 크기 마다 유지하기 어렵다 그래서 scss를 사용한다
- scss 는 디자인을 유지해준다 ex) disply:flex

### 1. flex box(flex)

- children과 얘기하지않고 자식과 항상 붙어있는 부모에게 명령어를 적용한다 (부모가 flex container가 된다)

### 2. main axis and cross axis 

- flex container의 flex-direction **기본값은 row** 이다
  - row (행) 가로 / column(열) 세로
-  flex-direction : row    =     main axis : 가로     =   기본방향 :가로   = cross axis : 세로
- **justify-content**은  **main axis방향**(가로축)으로 item옯길때 사용
  - justify-content: space-between (box사이에 공간을 줌)

​                                          space-around (box주변 옆공간을 같게 만듦)

-  **align-items**은 **cross axis 방향으로**(세로축) item옮길때 사용
  - align-items: stretch (세로로 늘어남 그래서 children의 높이 값을 주면 안됨) 
  - align-items: center (부모와 아이의 높이가 같으면 center인지 구분 안감(이미 센터이다) 그래서 부모에게 높이를 주면 구분이감)

### 3. Column and Row

- flex-direction : column   =   main axis : 세로   =   cross axis : 가로
  - justify-content :세로축
  - align-items : 가로축
  - flex-direction에 따라 main 과 cross 방향을 변경하고 싶다면 부모에게 높이를 줘야됨 그래야 구분이감

### 4. align-self and order

- align-self는 **부모에게 반드시 높이**를 줘야 적용가능하고 오직 자식에게만 줄수있는 기능이다 한 box에게만 해당된다
- order는 box에게 순서를 변경하라고 할수 있다
  - 기본적으로 box의 order 순서는 0 -> 1 -> 2 ->3 -> ......이다
  - order 지정을 안한 box는 0이고 1순위이다
  - HTML를 수정할수 없을때 유용함

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
   
     <style>
      .father {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 500px;
        font-size: 60px;
      }
      .child {
        width: 200px;
        height: 200px;
        background: peru;
        color: white;
      }
      .child:nth-child(1) {
        order: 1;
        align-self: center;
      }
      .child:nth-child(2) {
        order: 2;
      }
    </style>
      
  </head>
  <body>
    <div class="father">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
    </div>
  </body>
</html>
```

### 5. nowrap, warp, reverse, align-content

- nowrap

​    -  flex-wrap 기본값은 nowrap 이다

- wrap

​     - flex-wrap:wrap 라고 입력하면  flex에게 자식의 크기를 유지하라고 명령함

​     - flex box는 width 값을 무시하고 한줄에 다넣어 버린다

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="styles.css" />
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
       .father {
            display: flex;
            justify-content: space-around;
            height: 100vh;
            flex-wrap: wrap;
             }
        .child {
        width: 200px;
        height: 200px;
        background: peru;
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 60px;
        }
 
    </style>
  </head>
  <body>
    <div class="father">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
      <div class="child">6</div>
      <div class="child">7</div>
    </div>
  </body>
</html>
```

- reverse

  - flex-direction의 기본값은 row 이다 
  - row-reverse는 가로축에서 반대 반향으로 시작하는 것 (오른쪽에서 시작 ←)
  - column-reverse는 세로축에서 반대반햐응로 시작하는 것 (밑에서부터 시작 ↑)
  - flex-wrap: wrap-reverse는 wrap한 상태에서 원래값에서 반대반향으로 시작함(  2 →      

  ​                                                                                                                                                1 →   )

```css
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
  flex-wrap: wrap;
  flex-direction: row-reverse; 
  flex-direction: column-reverse;
```

- align-content
  - 위아래 박스들 사이공간을 수정할때 사용 (line 수정이다) , cross axis이다
  - align-content: flex-start 는 줄 나누는 공간이 없어진다 

```css
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
  flex-wrap: wrap;
  align-content: flex-start;
}
```

### 6. flex-grow, flex-shrink 

- (반응형 디자인할때 유용함)

- flex-shrink

  - 자식에게만 줄수있는 명령어다 
  - flex-shrink:1 기본값이다 (숫자가 늘어날수록 지정된 박스는 화면이 작아질때 다른박스들 보다 그 값만큼 더 작아진다 )

  ```css
  .child:nth-child(2) {
    flex-shrink: 2;
    background: black;
  }
  ```

- flex-grow
  - 주변에 자기가 차지할 수 있는 공간을 가지고 그값만큼 커진다 ,공간이 없으면 커질수없음 (주변공간을 가져감)
  - 기본 값은 flex-grow:0 이다

```css
.child:nth-child(2) {
  flex-grow: 2;
  background: black;
}
```

### 7. flex-basis

- 자식에게만 적용
- width 와 같은 속성이다 (flex-direction: row 일때 수평으로 적용함, main axis)
- height 일때도 있다 (flex-direction: column 일때 수직으로 적용함, cross axis)

```css
.father {
  display: flex;
  justify-content: space-around;
  width: 100%;
  height: 100vh;
}
.child {
  flex-basis: 20%;
  background: peru;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;
}

.child:nth-child(2) {
  flex-grow: 1;
  background: black;
}
```

### **`justify-content`** (가로)

- `flex-start`: 요소들을 컨테이너의 왼쪽으로 정렬합니다
- `flex-end`: 요소들을 컨테이너의 오른쪽으로 정렬합니다
- `center`: 요소들을 컨테이너의 가운데로 정렬합니다
- `space-between`: 요소들 사이에 동일한 간격을 둡니다
- `space-around`: 요소들 주위에 동일한 간격을 둡니다

### **`align-items`(세로)**

- `flex-start`: 요소들을 컨테이너의 꼭대기로 정렬합니다
- `flex-end`: 요소들을 컨테이너의 바닥으로 정렬합니다
- `center`: 요소들을 컨테이너의 세로선 상의 가운데로 정렬합니다
- `baseline`: 요소들을 컨테이너의 시작 위치에 정렬합니다
- `stretch`: 요소들을 컨테이너에 맞도록 늘립니다

### `**flex-direction`(정렬해야 할 방향을 지정)**

- `row`: 요소들을 텍스트의 방향과 동일하게 정렬합니다
- `row-reverse`: 요소들을 텍스트의 반대 방향으로 정렬합니다
- `column`: 요소들을 위에서 아래로 정렬합니다
- `column-reverse`: 요소들을 아래에서 위로 정렬합니다

### `order` (순서)

- order의 기본 값은 0이며, 양수나 음수로 바꿀 수 있습니다
- -2 >-1 >0 >1 >2    ( -2가 제일 우선순위이다  )

### **`align-self`** (개별)

- 개별 요소에 적용할 수 있는 또 다른 속성입니다
- 그 값들은 지정한 요소에만 적용됩니다
- align-items값들과 같다

### **`flex-wrap`**

- `nowrap`: 모든 요소들을 한 줄에 정렬합니다.
- `wrap`: 요소들을 여러 줄에 걸쳐 정렬합니다.
- `wrap-reverse`: 요소들을 여러 줄에 걸쳐 반대로 정렬합니다.

### `flex-flow`

- `flex-direction`과 `flex-wrap`이 자주 같이 사용되기 때문에, `flex-flow`가 이를 대신할 수 있다
- `flex-flow:column wrap` 세로선상에서 여러줄 걸쳐 정렬
- ` flex-flow: row wrap` 가로선상에서 여러줄 걸쳐 정렬

### **`align-content`**

- 여러 줄 사이의 간격을 지정할 수 있습니다
- `flex-start`: 여러 줄들을 컨테이너의 꼭대기에 정렬합니다.
- `flex-end`: 여러 줄들을 컨테이너의 바닥에 정렬합니다.
- `center`: 여러 줄들을 세로선 상의 가운데에 정렬합니다.
- `space-between`: 여러 줄들 사이에 동일한 간격을 둡니다.
- `space-around`: 여러 줄들 주위에 동일한 간격을 둡니다.
- `stretch`: 여러 줄들을 컨테이너에 맞도록 늘립니다.

## GRID

grid 규칙은 flexbox와 비슷하다

grid design는 부모에게 해야됨  ( display:grid )

### 1. grid-template-columns

```css
.father {
  display: grid;
  grid-template-columns: 250px 500px 250px;
}
```

  grid-template-columns: 250px 500px 250px; column너비 (좌우) 값을 나타냄(3개)

### 2.grid-template-row

```css
.father {
  display: grid;
  grid-template-rows: 250px 100px 300px 50px;
}
```

 grid-template-rows  : row너비(상하)값을 나타냄(4개)

### 3.row-gap / column-gap / gap

```css
.father {
  display: grid;
  grid-template-columns: 250px 250px 100px;
  grid-template-rows: 100px 50px 300px;
  row-gap: 10px;
  column-gap: 10px;
}
```

row-gap: 10px;    (상하간격)    / column-gap: 10px;  (좌우간격)  / gap (상하좌우간격)

### 4.repeat(   ,      px)

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 200px);
```

 grid-template-columns: repeat(4, 200px); 

 = 

 grid-template-columns: 200px 200px 200px 200px;

- css grid가 가진 함수 이다 .
- 200px 값으로 4번 반복한다는 뜻

### 5. grid-template-areas

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  grid-template-rows: 100px repeat(2, 200px) 100px;
  grid-template-areas:
    "header header header header"
    "content content content nav"
    "content content content nav"
    "footer footer footer footer";
}

.header {
  background-color: greenyellow;
  grid-area: header;
}
.content {
  background-color: blue;
  grid-area: content;
}
.nav {
  background-color: darkgoldenrod;
  grid-area: nav;
}
.footer {
  background-color: salmon;
  grid-area: footer;
}
```

- grid-area에 있는 이름과 grid-template-areas가 같아야됨
- class와 별개로  grid-area로 이름 지정해줘야됨

### 6. grid-column-start/grid-column-end

```css
.content {
  background-color: blue;
  grid-column-start: 1;
  grid-column-end: 4;
  grid-row-start: 2;
  grid-row-end: 4;
}
```

- start와 end 는 column이 아니고 line을 얘기하는거다
- 1번재 줄에서 시작하고 5번째 줄에서 끝난다는 이야기이다 column순서와 무관함
- 이걸사용하면 areas 안하게됨

### 7.shortcuts (시작/끝)

- start와 end 를 같이 적을수 있다

```css
.nav {
  background-color: darkgoldenrod;
  grid-row: 2/4;
}
```

- 몇개의 line이 있는지 신경쓰지 않고 적용할수있다 
  - 1(처음시작)  / -1(끝이라는 의미)  / -2(마지막 전)  /....

```css
.nav {
  background-color: darkgoldenrod;
  grid-row: 2/-2;
}
.footer {
  background-color: salmon;
  grid-column: 1/-1;
}
```

- span 을 사용할수있다

  - span은 수직,수평 모두 작용하고 시작과 끝점을 적는 걸 대신할수있다

  - 얼마큼 cell을 가지고 있는지 입력하기만 하면됨 (ex: span 4 )

```css
.nav {
  background-color: darkgoldenrod;
  grid-row: span 2;
}
.footer {
  background-color: salmon;
  grid-column: span 4;
}
```

### 8.Line Naming

- line에 이름을 붙여서 사용

```css
.grid {
  display: grid;
  gap: 10px;
  grid-template-columns: [first-line]100px [second-line]100px[third-line]100px[fourth-line]100px[fifth-line]100px;
  
    grid-template-rows: repeat(4, 100px);
}
.content {
  background-color: blue;
  grid-column: first-line/fourth-line;
  grid-row: span 2;
}
```

### 9. fr (fraction)

- grid에서 사용가능한 공간을 말해주는 측정단위임
  - gride에서 width가 500px이면 그안에서 부분이 나눠짐
  - grid container 안에서 얻은 공간이다
  - 유연한 layout 을 할수있다(화면 크기에 상관없이 비율이 유지됨)
  - (4fr 1fr 1fr 1fr) : 4fr는 4배더큰 공간을 말함  
  - (4, 1fr) 4번 똑같이 나눈다는 뜻
  - 가로는 화면의 크기이지만 수직은 공간이 없다 0이다 그래서 높이 설정을해야됨 (ex: 50vh 화면의 절반크기)

### 10. Grid Template

- grid-template에서 grid-area이름을 사용할것이다

- grid-template작성하는법 (여기서는 repeat 함수 적용 안된다 )

  "row의 이름 작성"  row의 높이작성 (fr)

  그리고 마지막에 "/" 를 적고 column마다 폭이(width) 얼마나 되는지 적어야됨

  (/ fr fr fr fr)

```css
.grid {
  display: grid;
  gap: 10px;
  height: 50vh;
  grid-template:
    "header header header header" 1fr
    "content content content nav" 2fr
    "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr;
}

.header {
  background-color: greenyellow;
  grid-area: header;
}

.content {
  background-color: blue;
  grid-area: content;
}
.nav {
  background-color: darkgoldenrod;
  grid-area: nav;
}
.footer {
  background-color: salmon;
  grid-area: footer;
}

```

### 11. place items

- items 는 각 사각형 하나하나에 어떤걸 적용하는지 의미한다 

- stretch는 grid-container가 grid를 갖고 있고 늘여서 grid자체를 채우도록 한다

- justify-items의 기본값은 stretch이다 (수평)

- align-items의 기본값은 stretch이다 (수직)

- 기본크기를 (높이와 너비)를 정해주면 stretch는 적용이 안된다

- div의 높이와너비 =  text글자 (text가 있기때문에 div의 크기가 보이는것)

```css
.grid {
  display: grid;
  gap: 10px;
  height: 50vh;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  align-items: stretch;
  justify-items: center;
}
```

- align-items: stretch +  justify-items: center = place-items: stretch center
  - place-items : 수직 수평으로 작성한다

```css
.grid {
  display: grid;
  gap: 10px;
  height: 50vh;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  place-items: stretch center;
}
```

### 12. place content

- content 전체 grid이다, 모든 사각형을 다같이 함께 움직임

- justify-content는 grid전체를 를 움직이는 것 (수평)-column열로 움직임

-  align-content 는  grid전체를 를 움직이는 것 (수직)-row행으로 움직임

- stretch 는 값이 정해져있으면 적용이 안된다 100px: X / 1fr: O 이렇게 하면 적용됨 
- align-content: **stretch**;    →  grid-template-rows: repeat(4, **1fr**);

```css
.grid {
  background: gray;
  color: white;
  display: grid;
  gap: 5px;
  height: 250vh;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 1fr);
  justify-content: center;
  align-content: stretch;
}
```

- ` place-content: stretch center = `

​      `수직+수평=`

​      `align-content: stretch+ justify-content: center` 

```css
.grid {
  background: gray;
  color: white;
  display: grid;
  gap: 5px;
  height: 250vh;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 1fr);
  place-content: stretch center;
}
```

### 13. Place-self

- place-self: 수직 수평 
- 자식에게만 적용된 property이고 오직 한개만 적용된다

```css
.header {
  background-color: greenyellow;
  align-self: end;
  justify-self: center;
}
```

- ` place-self: end center = `

​       `수직+수평=`

​      ` align-self:end + justify-self:center`

```css
.header {
  background-color: greenyellow;
  place-self: end center;
}
```

### 14. Auto column / Auto row

```css
.grid {
  color: white;
  display: grid;
  gap: 5px;
  grid-template-columns: repeat(4, 100px);
    
  grid-template-rows: repeat(4, 100px);
  grid-auto-rows: 350px;
}
```

- **grid-auto-rows** : 만약 여기에 더많은 content가 있으면 자동으로 줘서 row를 생성함

-  **grid-auto-columns** : 더많은 content가 있으면 자동으로 줘서  column을 생성

-  grid-template-rows: repeat(4, 100px);
   		 grid-auto-rows: 350px;

  =    4 row 까지는 100px 이고  5 row부터는 350px이라는 뜻 

```css
.grid {
  color: white;
  display: grid;
  gap: 5px;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
  grid-auto-columns: 100px;
}
```

- **grid-auto-flow**:column : 더많은 content가 나오면 column으로 생성함

### 15. minmax

-  얼마나 작게 혹은 크게 element가 될수있는지 지정할수있도록 해줌
- 내용이 줄어들더라도 너무 많이 안 줄어 들었으면 좋을때 사용하기 좋음

```css
grid-template-columns: repeat(8, minmax(100px, 1fr));
```

```css
grid-template-columns: repeat(8, minmax(100px, 200px));
```

minmax (최소크기, 최대크기)

### 16. auto-fit / auto-fill

```css
.grid:first-child {
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}
.grid:last-child {
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
```

- auto-fill : 더많은 공간을 가진다. 정확한 사이즈를 위해서 사용 
- auto-fit : 빈공간을 만들지 않음, 유동적인 사이즈를 위해서 사용

### 17. min-content  /  max-content

- 의미하는 것은 크기이다
- min-content: 만약 box를 만든다고 하면 content가 작아질수 있는 만큼 작아짐
- max-content: 만약 box를 만든다고 하면 content가 필요한 만큼 크게 만듦

```css
 grid-template-columns: max-content min-content;
```



## `grid-column-start` ##

- 그리드 요소의 시작 열(column)위치를 지정함 (line)
- ex)     grid-column-start: 3;

## `grid-column-end`

- 그리드 요소의 마지막 열(column)위치를 지정함  (line)
- ex)     grid-column-end: 4;

## `grid-column-start / grid-column-end`

- `grid-column-start` 와 `grid-column-end`를 같이 사용할때, 

  시작 값보다 마지막 값이 더 커야한다고 생각하실 수 있습니다. 하지만 꼭 그렇지만 않다

  ```css
  grid-column-start: 5;
  grid-column-end: -5
  ```

- 그리드 왼쪽의 기준이 아닌 오른쪽으로 기준을 하고싶다면, 

  `grid-column-start` 와 `grid-column-end`를 음수로 설정하면됨

  예를들어, -1로 오른쪽 첫뻔째 세로선을 지정하실 수 있다

  ```css
  grid-column-start: 1;
  grid-column-end: -2
  ```

-  `span`을 이용하여 열(column)의 넓이를 지정할 수 있습니다. `span`은 양수만 설정 가능합니다.

  ```css
  grid-column-start: span 3
  grid-column-end: 6;
  ```

## `grid-column / grid-row`

- 매번 `grid-column-start`와 `grid-column-end`를 입력하는 것은 불편하다 그래서

  `grid-column`는 한번에 입력가능하다, /(슬래쉬)로 구분된다

  ```css
   grid-column: 4/6
  ```

  ```css
  grid-column:2/span 3
  ```

  ```css
  grid-column: 2;
  grid-row: 5;
  ```

## `grid-area`

- /(슬래쉬)로 구분지어 

  `grid-row-start`, `grid-column-start`, `grid-row-end`, `grid-column-end`순으로 입력함

  ```css
  grid-area: 1/2/4/6;
  ```

## `order`

-  그리드의 모든 요소들은 `order`의 값이 0이지만, `z-index`와 같이 양수와 음수의 값 모두 설정이 가능

  ```css
  order:1;
  ```

## `grid-template-columns/grid-template-rows `

```css
grid-template-columns: 50% 20% 20% 20% 20%;
grid-template-rows: 20% 20% 20% 20% 20%;
```

## `repeat`

- 동일한 너비의 열이나 행을 지정할려면 불편하다 그래서 repeat 함수가 이 문제를 해결해줌

  ```css
  grid-template-columns: repeat(5,20%);
  ```

## `fr`

- `fr` 단위들은 사용가능한 공간을 하나로 공유하여 할당함

- 예시로 두개의 element들을 `1fr`과 `3fr`로 설정시, 공간이 4개의 동일한 크기로 공유됨

  첫번째 element는 사용가능한 공간의 1/4 크기로 그리고 두번째 element는 3/4 크기를 차지함

  ```css
  grid-template-columns: 1fr 5fr
  ```

  ```css
  grid-template-columns: 50px repeat(3, 1fr) 50px ;
  ```

## `grid-template`  : 행/열 

-  `grid-template-rows`와 `grid-template-columns`를 조합한 단축 속성

- 예를 들어, `grid-template: 50% 50% / 200px;`은 ( grid-template: 행 행/열)

  각각 50% 인 두개의 행(row)과 200px 너비의 한개의 열(column)의 그리드를 생성합니다.

```css
grid-template: 60%/ 200px
```

- auto는 가능한 많은 행을 많들고 50px는 맨마지막 행에 값을 적용한다 /1fr 4fr는 열이다 

```css
grid-template: auto 50px/ 1fr 4fr
```

## SCSS

1. crtl+~
2. npm run dev 엔터해서 실행

### 1. variable  (_variables.scss)

- 기본적으로 websit에서 가장중요한 color나 중요한 style을 저장하고 싶을 때 쓴다
- _variables.scss 이름을 가진 파일을 만든다 (밑줄 _ 이 있는 파일들은 css로 변하지 않았으면  하는 것들이다)
  - 그래서 _ 밑줄의 의미는 scss만을 위한 파일이란 의미이다

- $ 이름 :값;  

  - ```scss
    $fontMedium: 22px;
    ```

- styles.scss 에서 import 하기  `*@import* "_variables.scss";` 

- styles.scss  에서 값을 넣어주기

  - ```scss
    p {
      font-size: $fontMedium;
    }
    ```

### 2. Nesting

```scss
.box {
  margin-top: 20px;
  &:hover {
    background-color: green;
  }
  h2 {
    color: blue;
  }
  button {
    color: red;
  }
}
```

-  box안에 &은 자기자신을 뜻함 , box안의 h2의 의미는 html에서 box안에 h2 라는뜻

### 3. Mixins

- 상황에 따라 다르게 코딩을 하고 싶으면 사용하는 것

- _mixins.scss 파일따로 만들기

- _mixins.scss 파일에서 `@mixin 이름 {   } ;`

  - ```scss
    @mixin sexyTitle {
      color: blue;
      font-size: 30px;
      margin-bottom: 12px
    }
    ```

- `@import "_mixins.scss";` 으로 styles.scss에서 import 하기 

- styles.scss  에서 값을 넣어주기

  - ```scss
    h1{
     @include sexyTitle
    }
    ```

**@mixin의 링크에 값을 넣는 방법**

- sexyTitle에게 $color라는 variable을 링크에 넣는 방법 

```scss
@mixin sexyTitle($color) {
  color: $color;
  font-size: 30px;
  margin-bottom: 12px
}
```

- styles.scss 에 값넣기           (       ($color)= (blue) 그래서 글자 색은 블루가 된다      )

```scss
h1{
 @include sexyTitle(blue);
}
```

**@mixin의 링크에 값을 넣고 if else 다루는 방법**

```scss
@mixin link($word) {
  font-size: 30px;
  margin-bottom: 12px
  @if $word == "odd"{
   color: blue;
  }@else{
   color: red;
  }
}
```

- 만약 $word의 값이 odd이면 글자색은 blue이고  $word의 값이 odd가아니면 글자색은 red이다

```scss
a{
 @include link("even");
}
```

- even 이기때문에 글자색은 red가 된다 

### 4. Extends

- 같은 코드를 중복하고 싶지않을때 사용

- scss 파일을 하나 만든다 

- _buttons.scss파일에서 `% 이름 {    };` 만들기 

  - ```scss
    %button{
     border-radius: 7px;
     font-size: 12px;
     padding: 5px 10px
    }
    ```

- `@import "_buttons.scss";` 으로 styles.scss에서 import 하기

- styles.scss 에서 원하는 곳에 값넣기

  - ```scss
    a{
     @extend %button;
    }
    button{
      @extend %button;
    }
    ```

### 5. Mixins and Conclusions 

- _mixins.scss파일 하나 만들고 styles.scss 에게 @import 해준다 

- _mixins.scss파일에서 `@mixin 이름 {  };`

  - ```scss
    @mixin responsive{
      @content;
    }
    ```

- styles.scss에서 값을 넣어주기

  - ```scss
    a{
     @include responsive{
      text-decoration: none;
     }
    }
    ```

     text-decoration: none; = @content;

**반응형을 포함한 mixins**

```scss
$minIphone: 500px;
$maxIphone: 690px;
$minTable: $minIphone + 1;
$maxTable: 1120px;

@mixin responsive($devic) {
  @if $devic == "iphone" {
    @media screen and (min-width: $minIphone) (max-width: $maxIphone) {
      @content;
    }
  } @else if $devic == "tablet" {
    @media screen and (min-width: $minTable) and(max-width:$maxTable ) {
      @content;
    }
  } @else if $devic == "iphone-l" {
    @media screen (min-width: $minIphone) (max-width: $maxIphone) and(orientation:landscape) {
      @content;
    }
  } @else if $devic == "ipad-l" {
    @media screen (min-width: $minTable) and(max-width:$maxTable ) and(orientation:;:landscape) {
      @content;
    }
  }
}
```

- _mixins.scss파일에 반응형으로 만들기 

```scss
h1{
 color:red;
 @include responsive("iphone"){
  color:yellowl;
 }
    @include responsive("iphone-l"){
        font-size: 60px;
    } 
}
```

- styles.scss에 mixins 값사용하기 
- h1컬러가 빨간색이지만 mixins.scss에서 작성한 iphone크기 값이 되면 yellow색으로 바뀐다

- h1 크기가 iphone-l 값이되면 글자크기가 60px으로 바뀐다













































  
