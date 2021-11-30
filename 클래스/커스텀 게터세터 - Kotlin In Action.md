## 커스텀 getter/setter

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 커스텀 getter/setter

- 코틀린은 필드 선언 시 자동으로 getter/setter를 제공한다.
- 커스텀 getter/setter를 직접 작성할 수도 있다.
~~~kotlin
class Rectangle(val height: Int, val width: Int) {
    val isSquare: Boolean // 필드 선언, 정사각형인지 구분하기 위한 필드
        get() { // 커스텀 getter 작성
            retrun height == width
        }
}
~~~
- 위 코드 설명
  - isSquare 필드는 정사각형 여부를 저장하고 있는 필드이다.
  - 커스텀 getter를 작성했다.
  - `get() = height == width` 라고 작성해도 된다. (굳이 중괄호로 블록문 만들지 않아도 된다.)

<br></br>