## enum 클래스

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - enum 클래스란

- `enum class` = 이넘 클래스
- `enum` = `enumeration(열거)`의 줄임말
- 여러 개의 값을 관리해야 할 때 사용하는 클래스이다.
- 여러 개의 값을 열거(나열)하여 정의한다.
  - 값 = `enum 상수` 라고도 부른다.
- 단, 값을 열거만 하려고 존재하는 클래스는 아니다.
- enum 클래스 안에도 일반 클래스처럼 프로퍼티와 메소드를 정의할 수 있다.
- `enum class`라는 키워드를 사용해서 이넘 클래스를 정의한다.
- 각 enum 상수 사이는 `콤마(,)`로 구분한다.
~~~kotlin
enum class Color {
    RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET
}
~~~
- 위 코드 설명
  - 색상을 나타내는 이름의 값을 enum 상수의 모습으로 나열하고 있다.
~~~kotlin
enum class Color(val r:Int, val g:Int, val b:int) { // 프로퍼티 정의
    RED(255, 0, 0), // 값을 열거할 때 프로퍼티 값을 초기화하여 열거한다.
    ORANGE(255, 165, 0),
    YELLOW(255, 255, 0),
    GREEN(0, 255, 0),
    BLUE(0, 0, 255),
    IDIGO(75, 0, 130),
    VIOLET(238, 130, 238); // 세미콜론 사용하여 구분

    fun rgb() = (r * 256 + g) * 256 + b // 메소드 정의
}

fun main() {
    println(Color.RED.rgb()) // 사용 예시
    println(Color.YELLOW.rgb())
}
~~~
- 위 코드 설명
  - 각 enum 상수가 보유할 프로퍼티를 정의한다.
  - 상수를 정의할 때 프로퍼티에 해당하는 값을 초기화해준다.
  - enum 클래스 안에 메소드를 정의하는 경우,
  - 반드시 enum 상수 목록과 메소드 정의 사이를 `세미콜론`으로 구분해줘야 한다.

<br></br>

### 02 - enum 클래스 사용 예시

- 제어문(when)과 함께 사용할 수 있다.
  - 제어문과 함께 사용하는 예시 외에도 다양한 예시가 있을 수 있다.
- 무지개 색상(빨주노초파남보) 중 특정 색상이 몇 번째 색상인지 알려주는 함수를 작성해야 한다고 가정.
~~~kotlin
import com.chohee.example.Color // Color enum 클래스가 다른 패키지에 있을 경우 import 된다.(패키지는 예시임)

...

fun getOrderInRainbow(color: Color): Int = 
    when (color) {
        Color.RED -> 1
        Color.ORANGE -> 2
        Color.YELLOW -> 3
        Color.GREEN -> 4
        Color.BLUE -> 5
        Color.INDIGO -> 6
        Color.VIOLET -> 7
    }

fun main() {
    println(getOrderInRainbow(Color.GREEN)) // 4 출력된다.
}
~~~
- 위 코드 설명
  - 함수의 인자로 전달된 color 값이 enum 클래스에 정의해둔 색상 상수 값들 중 어떤 것과 매치되는지 확인한 후,
  - 매치된다면 해당 색이 몇 번째 색상인지 반환하는 함수이다.
- `Color.RED` 처럼 `enum class.상수` 라고 작성해야 하는게 길고 불편하다면,
- `import` 시 enum 상수를 모두 import 하면 된다.
~~~kotlin
import com.chohee.example.Color.* // *을 붙여 enum 상수를 한 꺼번에 보두 import 한다.

...

fun getOrder(color: Color): Int = 
    when (color) {
        RED -> 1 // Color.RED -> RED 로 짧게 작성 가능
        ORANGE -> 2
        YELLOW -> 3
        GREEN -> 4
        BLUE -> 5
        INDIGO -> 6
        VIOLET -> 7
    }
~~~

<br></br>

# 공부 끝~ 🏃🏻‍♀️