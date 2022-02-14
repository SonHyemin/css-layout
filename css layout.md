# css layout

scss 하기 위해서는 node.js 설치하기

## flex box

- disply:block 는 box 속성을 가짐, 그래서 옆에 아무도 올수 없고 세로로 나열함   ex) div
- disply:inline-block는 bpx 속성을 가짐, 그래서 block속성을 유지할수있게 해주고 가로로 나열함  (withd,height 적용 가능)
- inline-block 와 inline 차이점: inline은 box가 아니다 그래서 너비와 높이가 적용이 안된다
- css만으로 디자인을 디스플레이 크기 마다 유지하기 어렵다 그래서 scss를 사용한다
- scss 는 디자인을 유지해준다 ex) disply:flex

1. flex box(flex)는 children과 얘기하지않고 부모에게 명령어를 적용한다 (부모가 flex container가 된다)