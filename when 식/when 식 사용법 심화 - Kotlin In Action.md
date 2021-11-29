## when 식 사용법 심화

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 하나의 분기 안에서 매치 패턴 여러 개 설정하기

- 하나의 분기 안에서 여러 값을 매치 패턴으로 설정할 수 있다.
- `콤마(,)`를 사용하여 여러 매치 패턴을 작성해주면 된다.
~~~kotlin
fun isMyFavoriteColor(color: Color) = when (color) {
    Color.RED, Color.GREEN, Color.Blue -> true
    Color.INDIGO, Color.VIOLET -> false
}
~~~
- 위 코드 설명
  - 이 함수는 파라미터로 전달된 color 값이 빨강, 초록, 파랑 중 하나면 true를 반환한다.

<br></br>

### 02 - when 식의 분기 조건에 객체 사용하기

- 자바의 switch 문과 달리, 코틀린의 when 식에서는 분기 조건에 `상수` 뿐 아니라,
- `객체`도 허용한다.
- 두 개의 색을 섞으면 나오는 색을 반환하는 함수를 가정해보자.
~~~kotlin
fun mix(color1: Color, color2: Color) = 
    when (setOf(color1, color2)) {
        setOf(RED, YELLOW) -> ORANGE
        setOf(YELLOW, BLUE) -> GREEN
        setOf(BLUE, VIOLET) -> INDIGO
        else -> throw Exception("매칭 분기 없음")
    }
~~~
- 위 코드 설명
  - `setOf()` 는 코틀린 표준 라이브러리에서 제공하는 함수이고, 자료 구조 Set 객체를 만들어 반환하는 함수다.
  - 분기 조건 부분이 상수가 아니라 객체이다.
  - `Set(집합) 자료구조` = 원소들이 모여있는 구조이고, 모여있기만 하지, 각 원소의 순서는 중요하지 않다.
  - `setOf(RED, YELLOW) 분기 조건` = color1, color2가 순서 상관 없이 한 개가 RED이고 나머지 한 개가 YELLOW라는 것

# 공부 끝~ 🏃🏻‍♀️