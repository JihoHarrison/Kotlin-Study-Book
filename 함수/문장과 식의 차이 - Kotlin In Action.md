## 문장과 식의 차이

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 프로그래밍 언어에서 문장과 식의 차이

- `문장` = 문장은 자신을 둘러싸고 있는 가장 안쪽 블록의 최상위 요소로 존재하며 아무런 값을 만들어내지 않는다.
  - = statement
- `식` = 식은 값을 만들어 낸다.
  - = expression
- 자바에서는 모든 제어 구조(if문, switch 등)가 문장이다.
- 코틀린은 루프를 제외한 대부분의 제어 구조가 식이다.
- 제어 구조가 식이라는 점을 잘 활용하면 코드를 아주 간결하게 표현할 수 있다.
~~~java
// java
public int max(int a, int b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}
~~~
~~~kotlin
// kotlin
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
~~~
- 위 코드 설명
  - 위 if 문은 a 또는 b 값을 도출해내는 `식`이다.
  - `return` 키워드 뒤에는 반환할 `값`을 적어줘야 하기 때문에 값을 만들어내는 if 문 자체를 적을 수 있다.
  - 자바보다 코틀린에서의 코드 길이가 더 간결해졌다.

<br></br>