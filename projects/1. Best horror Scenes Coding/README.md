# 1.https://besthorrorscenes.com/

## - position

```scss
position: fixed;
top: 0;
left: 0;
```

positon 이 고정되어있다 위에서 왼쪽으로 

```scss
main {
  margin-left: $fixedwidth;}
```

왼쪽에 고정한 만큼 main에게는 margin-left를 준다 그래야 main이 보임

## -   letter-spacing

```scss
h1{
  letter-spacing: 5px;
}
```

글자간 간격 조절해줌

## -  line-height

```scss
h3,
p {
width: 70%;
line-height: 1.2;
text-align: justify;
}
```

문장간의 아래위 높이를 조절해줌

## -   flex-wrap

```scss
 ul {
      display: flex;
      flex-wrap: wrap;}
```

wrap 은 가능한 영역 내에서 벗어나지 않고 여러행으로 나누어 표현 

## - linear-gradient

```scss
 .movie {
    background:linear-gradient(to bottom,
        rgba(0, 0, 0, 0.1) 10%,
        rgba(0, 0, 0, 0),
        rgba(0, 0, 0, 0),
        rgba(0, 0, 0, 0),transparent),$red;
        }
```

4가지 변화를 가지고 있는 투명도 그라데이션이 red색상 위에서 이루어져 직선으로 밑으로 내려가는 그라데이션이다
