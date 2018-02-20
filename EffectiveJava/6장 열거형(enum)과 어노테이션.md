# 6장 열거형(enum)과 어노테이션

> 자바1.5에 추가된 `참조 자료형(reference type)`



### 규칙 30. int 상수 대신 enum을 사용하라



#### enum 자료형

```java
public enum Apple { FUJI, PIPPIN }
```

- 자료형의 개체 수는 엄격히 통제된다(규칙 1)
- 자바의 enum 자료형은 열거 상수별로 하나의 객체를 `public static final` 필드 형태로 제공하는 것

```java
// 방법 2
// toString 메서드 작동시 괄호 안에 적은 기호가 나온다
public enum Operation{
    PLUS("+")  //데이터
    { double apply(double x, double y){return x+y;} } ,  //  메서드 구현
    MINUS("-")   { double apply(double x, double y){return x-y;} },
    TIMES("*")   { double apply(double x, double y){return x*y;} },
    DIVIDE("/")  { double apply(double x, double y){return x/y;} };

    abstract double apply(double x, double y);
    Operation (String symbol) {this.symbol = symbol};
}
```

- 언제 enum 써야 하나 ?  -> 고정된 상수 집합이 필요할 때





###규칙  35. 작명패턴 대신 어노테이션을 사용하자

어노테이션은 어노테이션이 적용된 프로그램의 동작에는 개입하지 않음, 해당 어노테이션에 관심 있는  프로그램에게 유용한 정보를 제공할뿐임



**?**

- 리플렉션 `java.lang.reflect`
  - 리플랙션이란 클래스의 정보를 객체를 통해 분석해내는 프로그램 기법을 말한다
  - *리플렉션 기법의 프로그램 사용*
    - 메모리를 보유하고 있는 형을 모르는 객체 존재
    - 객체의 클래스 정보 알아낸다 `(.class, 즉 객체의 클래스 생성)`
    - 분석된 정보를 이용하여 멤버 메서드 멤버필드사용
  - *리플렉션의 기법*
    - 클래스의 능력을 객체를 통해서 런타임 시에 분석한다.
    - 객체들을 런타임 시에 검사한다.





###규칙 37. 자료형을 정의할때는 표식 어노테이션 대신 표식 인터페이스를 사용해라

- **표식 인터페이스(Marker Interface)**
  - 아무 메서드도 선언한지 않는 인터페이스
  - 표식 인터페이스 의 예: `Serializable`. 아무일도 하지 않지만, 이 인터페이스 임을 보고 `OutputObjectStream` 객체가 처리. 다만 설계상의 오류는, `write` 함수가 `Serializable` 인터페이스가 아니라 `Object` 를 인자로 받음.