## 패키지, import 문

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 코틀린의 패키지 개념

- `package` = 패키지
- 코틀린 파일의 가장 상단에 `package` 키워드로 시작하는 문을 넣을 수 있다.
~~~kotlin
// Example.kt
package geometry.shapes

...
~~~
- 파일 상단에 패키지문으로 패키지를 선언하면,
- 해당 파일 안에 작성된 모든 `클래스`, `함수`, `프로퍼티` 등이 해당 패키지에 속하게 된다.
- 서로 다른 파일이 같은 패키지에 속해 있으면,
- 서로 다른 파일에서 정의한 클래스, 함수, 프로퍼티 일지라도 직접 사용할 수 있다.(import 없이)
- 다른 패키지에 속해 있는 것을 사용하려면,
- `import` 선언을 통해 불러와야 한다.
~~~kotlin
package geometry.shapes // 패키지 선언

import java.util.Random // 표준 자바 라이브러리 클래스를 임포트.

class Rectangle(val height: Int, val width: Int) {
    val isSquare: Boolean // 프로퍼티 선언
        get () = height == width // 커스텀 접근자
}

fun createRandomRectangle(): Rectangle {
    val random = Random()
    return Rectangle(random.nextInt(), random.nextInt())
}
~~~
- 위 코드 설명
  - 위 파일이 속해 있는 패키지는 `geometry.shapes` 이다.
  - 다른 패키지에 속해 있는 `random.nextInt()` 함수를 사용하기 위해
  - `import` 문으로 Random 클래스를 임포트했다.

<br></br>

### 02 - import 문

- 코틀린에서 `import` 키워드는 클래스, 함수, 프로퍼티 등 다른 패키지에 속해 있어 불러와야 하는 모든 대상에 대해 사용할 수 있다.
- 패키지 이름 뒤에 `.*` 을 추가하면 패키지 안의 모든 것들을 한 꺼번에 임포트할 수 있다.
  - 같은 패키지에 있는 다양한 클래스나 함수를 한 꺼번에 임포트한다.
~~~kotlin
package geometry.example

import geometry.shapes.createRandomRectangle // 특정 함수 임포트

fun main() {
    println(createRandomRectangle().isSquare)
}
~~~

<br></br>