## 클래스

공부 자료 : Kotlin In Action 2장 - 코틀린 기초

<br></br>

### 01 - 자바의 클래스 기본 구조

- 객체지향 프로그래밍에서 `클래스`라는 개념의 목적은 `데이터를 캡슐화`하는 것이다.
  - `encapsulate` = 캡슐화
- 자바에서는 데이터를 `필드(field)`에 `저장`한다.
- 멤버 필드는 보통 `비공개(private)`이다.
- 클래스는 자신을 사용하는 클라이언트가 필드에 접근할 수 있도록 `getter(게터)`를 제공한다.
- 필드의 값을 변경하게 허용해야 할 경우 `setter(세터)`를 추가로 제공한다.
- `프로퍼티(property)` = 필드와 getter/setter를 묶어서 프로퍼티라고 부른다.
- 자바에서는 선언되는 프로퍼티의 개수가 두 개 이상으로 늘어나면,
- 생성자 함수의 파라미터 수도 늘어나고, 생성자 함수 본문에서 대입문의 수도 늘어난다.
~~~java
/* java */
public class Person {
    private final String name; // 프로퍼티
    private final Int age; // 프로퍼티

    public Person(String name, Int age) { // 생성자 함수
        this.name = name; // 대입문
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public Int getAge() {
        return age;
    }
}
~~~
- 위 코드 설명
  - Person 이라는 클래스 내에 선언된 필드는 name과 age 2개이다.
  - 생성자 함수의 파라미터로 전달된 데이터를 name과 age에 저장한다.

<br></br>

### 02 - 코틀린 클래스의 기본 구조

- 코틀린은 언어 자체적으로 프로퍼티를 제공한다.
- = 필드만 선언하면 getter/setter가 기본으로 제공된다.
- = 코틀린에서는 자바로 작성된 동일한 클래스를 만드는데 더 적은 코드가 사용된다.
- 필드 선언은 변수 선언 방법과 비슷하게 `val` 또는 `var` 키워드를 사용한다.
- `val` 키워드로 선언한 필드 = 읽기 전용
- `var` 키워드로 선언한 필드 = 읽기/변경 가능
- 필드는 기본적으로 비공개이다.
~~~kotlin
/* kotlin */
class Person {
    val name: String, // 비공개, 읽기 전용, getter 제공
    var isMarried: Boolean // 비공개, 변경 가능, getter/setter 제공
}
~~~
- 위 코드 설명
  - 자바에서는 `class` 키워드 앞에 붙이던 `public` 키워드가 코틀린에서는 없어졌다.
  - 코틀린에서는 클래스가 `public`이 기본이기 때문에 생략해도 된다.
  - 필드 선언 시 앞에 붙이던 `private` 키워드가 없어졌다.
  - 코틀린에서는 기본적으로 필드가 비공개이기 때문에 생략해도 된다.
  - 코드 상 보이지는 않지만 내부적으로 구현된 getter/setter가 제공된다.

<br></br>

### 03 - getter/setter 이름 규칙 예외

- 필드 이름이 `is` 로 시작하면,
- 해당 필드의 getter는 `get`으로 시작하지 않고, 필드의 이름 그대로가 getter의 이름이 된다.
- setter는 `is`를 `set`으로 바꾼 이름이 사용된다.
~~~kotlin
/* kotlin */
class Person {
    ...
    var isMarried: Boolean 
}
~~~
- 위 코드 설명
  - isMarried의 getter는 `isMarried()`이다.
  - setter는 `setMarried()`이다.

<br></br>

### 04 - 코틀린 클래스 사용하기

- `new` 키워드를 사용하지 않고 생성자를 호출한다.
- getter 호출은 필드 이름을 그대로 사용해도 된다.
- setter 호출은 필드에 데이터를 대입하는 식으로 대신할 수 있다.
~~~kotlin
val person = Person("jihoKevin", false) // 생성자 호출, new 사용 안 함

println(person.name) // getter 호출, jihoKevin 출력
println(person.isMarried) // getter 호출, false 출력

person.isMarried = true // setter 호출
~~~

<br></br>