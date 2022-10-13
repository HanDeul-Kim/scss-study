# css 전처리기 scss 정리

1. scss
   * sass를 사용 하면 css로 컴파일 해주어야함
    scss는 sass의 3번째 버전으로 css 구문과 완전히 호환되도록 새로운 구문을 도입.
    간단한 차이로는 중괄호와 세미콜론의 유무. sass(무), scss(유)

2. 실행
   * npx parcel url/index.html

3. 데이터 타입
   * number = 1,2em ...
   * string = bold, absolute, "./img/main.png" ...
   * color = red, tomato ...
   * booleans = true & false
   * nulls = null
   * lists = 공백이나 ,로 구분된 값의 목록 <br>**ex) (apple, banana, orange) or apple banana orange 가로 열고 닫고 자유**
   * maps = list와 유사하나 값이 key : value 형태 <br>**ex) (apple : a, banana : b) 꼭 가로 열어야함**

4. 중첩 ([참고](https://handeul-kim.github.io/scss-study/style.scss))
    * &(상위 선택자 참조)
      * 중첩 안에서 & 키워드는 상위(부모) 선택자를 참조하여 치환. <br>**ex) &.active일때 active의 className이 붙으면 처리할 css**
    * @at-root (중첩 벗어나기)
      * 부모의 자식으로 정의 되지 않은 밖의 엘리먼트를 부모 중첩에서 사용하고 싶을때 @at-root 키워드 사용한다. 부모에서 정의 된 변수도 사용 가능.
    * 중첩된 속성 정의
      * font, margin, padding 등과 같이 동일한 네임 스페이스를 가지는 속성들을 축약 해서 사용 가능.

5. 변수
    * 기본문법
      * 반복적으로 사용되는 값을 변수로 지정할 수 있다. 재선언도 가능.**ex) $변수이름: 속성값;**
    * 변수의 유효범위
      * 변수를 어떤 부모클래스에서의 안에서 선언하게 된 경우 부모의 중괄호 안에서만 사용 가능. (하지만 그렇다 하여도 따로 설정해서 사용할 수는 있다. global 전역 설정 항목 참고)
      * 어떤 특정 클래스에서 선언하지 않고 최상단이라던지 그러한 위치에서 선언한 경우 전역에서 사용 가능.
    * 변수 재할당
      * 기존에 만든 변수의 값을 새로운 변수의 값에 넣을수 있다.<br> **ex) $color-old: #fff라는 변수를 만들어놓고 새로운 변수 $color-new: $color-old**
    * !global (전역으로 설정)
      * !global 플래그를 사용하면 변수의 유효범위를 전역으로 설정할 수 있다.<br>(특정 클래스에서 선언한 변수여도 밖의 다른 태그 클래스도 적용 됨.)<br>**ex) $global-test: orange !global;**
    * !default (초깃값 설정)
      * !default 플래그는 할당되지 않은 변수의 초깃값을 설정한다. 즉, 할당되어있는 변수가 있다면 변수가 기존 할당 값을 사용한다.
    * ${} 문자 보간
      * #{}을 이용해서 코드의 어디든지 변수 값을 넣을 수 있다. ES6의 템플릿 리터럴과 유사한 것 같다.
      * **ex) $test-text: unquote('product_img01')**<br>  **url("./img/#{test-text}.png")**
      * Sass의 내장 함수 unquote()는 문자에서 따옴표를 제거합니다.
6. 연산
    * 숫자, 문자, 논리연산자, 등 javascript 연산자와 비슷함. (scss파일 참고)
7. 재활용 (Mixins)
    * sass Mixins는 스타일 시트 전체에서 재사용 할 css 선언 그룹을 정의 한다.<br>Mixins는 **선언하기(@Mixin)와 포함하기(@include)** 두 가지로 만들어서(선언) 사용하기(포함)로 생각하면 좋다.