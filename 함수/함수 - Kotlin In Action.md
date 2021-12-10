## 함수

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 모든 프로그램을 구성하는 기본 단위인 함수와 변수

- 어떤 언어든, 프로그램을 구성하는 기본 단위는 `함수`와 `변수`다.
- 코틀린으로 프로그래밍을 하면 실제로 수많은 함수를 만들게 될 것이다.

<br></br>

### 02 - 코틀린 함수의 기본 구조

- 함수 선언은 `fun` 키워드로 시작한다.
- fun 다음에는 `함수 이름`이 온다.
- 함수 이름 뒤에는 `괄호 안`에 `파라미터 목록`이 온다.
- 괄호 뒤에는 `:` 를 써주고 함수의 `반환 타입`을 써준다.
~~~kotlin
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
~~~
- 위 코드 설명
  - 파라미터로 전달된 a와 b 중 큰 값을 반환하는 함수다.

<br></br>

### 03 - 식이 본문인 함수

- 위 코틀린 기본 구조 자체를 더 간결하게 작성할 수도 있다.
- 단, 함수의 본문이 `식(expression)`이여야 한다.
- 함수 본문을 감싸는 중괄호와 return을 제거하고, `등호(=)`를 식 앞에 붙인다.
~~~kotlin
fun max(a: Int, b: Int): Int = if (a > b) a else b
~~~
- 위 코드 설명
  - max() 함수는 본문이 if 식 하나로만 이루어져 있다.
  - 문장과 식의 차이를 알아야 한다.
- `블록이 본문인 함수` = 본문이 중괄호로 둘러싸인 함수
- `식이 본문인 함수` = 본문이 등호와 식으로 이루어진 함수
- 코틀린에서는 식이 본문인 함수가 자주 쓰인다.
- 본문 식에는 `단순한 산술식` 이나 `함수 호출` 뿐 아니라 `if`, `when`, `try` 등의 더 복잡한 식도 자주 쓰인다.
  - if 나 when 이 함수 본문에 들어가야 할 때는 식이 본문인 함수 형태로 나타낼 수 있는지 생각해보자.
- 식이 본문인 함수는 반환 타입을 생략할 수 있다.
- 코틀린은 정적 타입 지정언어이지만 `타입 추론`을 지원하기 때문이다.
- 식이 본문인 함수인 경우는 컴파일러가 식의 결과 값을 분석해서 반환 타입을 추론할 수 있다.
- 하지만 식이 본문인 함수에서만 반환 타입 생략이 가능하다.
~~~kotlin
fun max(a: Int, b: Int) = if (a > b) a else b // 가능, 반환 값 생략
~~~

<br></br>

### 04 - 함수를 최상위 수준에 정의할 수 있다.

- 자바와 달리 코틀린의 함수는 꼭 클래스 안에 넣을 필요가 없다.
~~~kotlin
/* MainActivity.kt 파일이라고 가정 */

// class 안에 함수를 넣지 않아도 된다.
fun main() {
    ...
}

class MainActivity {
    ...
}
~~~

<br></br>

### 05 - 람다 함수

 - 람다의 형식
    * 코틀린은 함수 호출 시 맨 마지막 인자가 람다식이면 이를 괄호 밖으로 빼낼 수 있다.
    ~~~kotlin
    people.maxBy() { p -> p.age }
    ~~~
    * 람다가 어떤 함수의 유일한 인자인 경우 함수 호출 괄호를 없애도 된다.
    ~~~kotlin
    people.maxBy { p -> p.age }
    ~~~
    * 람다의 파라미터가 하나뿐이고 그 타입을 컴파일러가 추론할 수 있는 경우 it을 바로 사용 할 수 있다.
    ~~~kotlin
    people.maxBy { it.age }
    ~~~
    
 - 람다의 Closure
    * 코틀린의 람다는 자바의 closure 개념과 다르다. 자바에서는 람다가 함수 내부에서 실행될 때, 로컬 변수에 접근하기 위해서는 해당 변수의 값이 final로 불변을 만족해야 한다.
      이는 Stack 영역에 로컬 변수의 메모리가 잡히고, 함수의 소멸과 함께 stack에서 pop(소멸)되기 때문이다.
      final인 경우 해당 변수 값을 그대로 복사해서 람다 내부에서 사용하며, 이를 `Lamda Captureing`이라고 한다.
    * 코틀린에서는 final이 아닌 로컬 변수에 접근하기 위해서 자바와는 다른 방식이 적용된다. 만약 final인 경우는 그대로 값을 복사하여 사용하지만 final이 아닌 변수의 경우, 코틀린에서 제공하는 Wrapper 클래스
      에 감싸지고, 이를 참조하여 접근하는 형식이다. 람다가 종료되어도 항상 변수의 참조 값을 람다 코드와 함께 저장한다.
    ~~~kotlin
    fun lambdaSample() { 
        var counter = 0 
        val inc = {counter++} 
        run {println(Inc)} 
    }
    ~~~
    
    * 위 코드는 counter의 값을 inc라는 상수에 넣어 접근라고 있으므로 정상적으로 동작한다. 아래 코드와 같이 Class로 Wrapping되어 동작하기 때문이다.
    ~~~kotlin
    class Ref<T>(var value: T)
    
    fun lambdaSample() {
        val counterWrapper = Ref(0)
        val inc = {counterWrapper.value++}
        run {println(Inc)
    }
    ~~~

    * 다음 코드는 결과값이 항상 0인 상태로 동작하게 된다. final 즉, 상수에 담아서 값을 그대로 가져오는 것이 아니기 때문에 함수가 끝나면서 `clicks`라는 변수는 다시 초기화 되게 된다.
    ~~~kotlin
    fun clickCount(button: Button): Int {
        var clicks = 0
        button.onclick { clicks++ }
        println(clicks)
    }
    ~~~
    <br><br>
 
