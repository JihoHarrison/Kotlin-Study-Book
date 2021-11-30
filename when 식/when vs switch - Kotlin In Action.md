## when vs switch

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 자바의 switch문

- switch 문으로 `전달된 값`과 `매치`되는 `분기`를 찾아서,
- 해당 분기의 `case` 로직을 수행한다.
- 가장 첫 분기부터 차례대로 매치되는지 계산하는 방식이다.
- 각 분기마다 `break`를 넣어줘야 한다.
- `break`를 빼먹으면 매치되는 분기의 case문을 실행한 후 switch문을 빠져나가지 못해서,
- 그 다음 분기와 매치되는지 또 계산하게 된다.
- 만약 그 다음 분기와 한 번 더 매치되는 경우, 해당 case문이 실행된다.
- 가장 마지막에 `default`을 통해 아무 분기와 매치되지 않을 경우 실행할 기본 로직을 작성할 수 있다.
- 개발자의 실수로 `break`문을 빠뜨려 원하지 않는 동작을 하는 경우가 종종 있다.
~~~java
// java
public static void main(String[] args) {
    String numberString = "";
    Int number = 3;
    switch (number) {
        case 1: numberString = "One";
                break;
        case 2: numberString = "Two";
                break;
        case 3: numberString = "Three";
                break;
        case 4: numberString = "Four";
                break;
        case 5: numberString = "Five";
                break;
        default: numberString = "Invaild number";
                break;
    }
    System.out.println(numberString) // Three 출력된다.
}
~~~
- 자바의 switch문을 코틀린에서는 `when` 으로 작성한다.
- 자바의 switch문에서는 분기 조건에 `상수(enum 상수나 숫자 리터럴 상수)`만 사용할 수 있다.

<br></br>

### 02 - 코틀린의 when

- `when`은 `식`이다. (문장이 아니다.)
  - `문장과 식` = 함수 폴더 > 문장과 식의 차이 문서 참고
- `식이 본문인 함수`에 `when`이 많이 사용된다.
- 자바와 달리 `break`를 작성하지 않아도 된다.
  - 코틀린 언어 내부적으로 각 분기마다 break 처리가 되어 있다.
  - break 빼먹는 실수로 인한 버그를 예방할 수 있다.
~~~kotlin
// 식이 본문인 함수에 사용된 when 예시
fun getNumberOfRainBow(color: Color) = when (color) {
    Color.RED -> 1
    Color.ORANGE -> 2
    Color.YELLOW -> 3
    Color.GREEN -> 4
    Color.BLUE -> 5
    Color.INDIGO -> 6
    Color.VIOLET -> 7
}
~~~

<br></br>