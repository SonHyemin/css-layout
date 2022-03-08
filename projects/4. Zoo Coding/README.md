# 4.https://z-o-o.fr/

## - 태그:not( )

```scss
   &:hover {
          li:not(:first-child) {
            color: white !important;
          }
        }
```

hover 적용시킬 태그는 li인데 first-child가 아닌 것만 적용한다

## - !important

```scss
  &:hover {
          li:not(:first-child) {
            color: white !important;
          }
        }
```

그전에 값은 무시하고 color를 white로 한다는 뜻

`!important`규칙을 사용하면 해당 요소의 특정 속성에 대한 모든 이전 스타일 지정 규칙을 재정의한다



