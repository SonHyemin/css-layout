# css layout

scss 하기 위해서는 node.js 설치하기

## flex box

- disply:block 는 box 속성을 가짐, 그래서 옆에 아무도 올수 없고 세로로 나열함   ex) div
- disply:inline-block는 bpx 속성을 가짐, 그래서 block속성을 유지할수있게 해주고 가로로 나열함  (withd,height 적용 가능)
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



