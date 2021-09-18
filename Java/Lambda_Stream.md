# Lambda expr/ Stream

## Lambda Expressions 람다식

### What is Lambda Expressions?

람다식 또는 람다 함수는 자바의 경우 1.8 버전에 추가된 기능.

본래 Lisp 등과 같은 함수형 언어에서 주로 사용되던 것으로 그.. 유명한 존 매카시가 도입.

익명함수 생성을 위한 것으로 결과를 집계, 병렬처리 등에 이점을 가지며 코드 또한 분량면에서 간결해진다는 장점을 가짐.

 

```java
XX xx = new XX()
{
	public void x1()
	{
		...
	}
};
```

위와 같은 코드가 존재할 때 람다식을 사용하면

```java
XX xx = () -> {...};
```

과 같이 함수의 형태로 간단하게 표현이 가능.

람다식의 코드는 (Parameter) -> {Execute Statement} 과 같은 형태로 작성, 런타임시 해당 인터페이스의 익명 객체로 생성.

### 기본 문법

```java
// 1
(String s) -> {System.out.println(ls);}

// 2
s -> {System.out.println(s);}

// 3
s -> System.out.println(s)

// 4
s -> {return x;};

// 5
s -> s
```

parentheses( ) 안에 타입과 파라미터를 기술하며 {  }안에 실행문을 작성.

 

위의 코드에서 1~3, 4~5는 기능적으로 동일.

변수 타입은 자동으로 인식 가능하므로 1에서 2처럼 생략이 가능하고, 실행문이 하나일 경우에는 2에서 3처럼 braces{ }  생략이 가능.

결과값 반환이 필요한 경우 명시하여 4의 형태로 기술 가능.

{ }안에 return 코드만이 존재할 경우에 다시 5의 형태로 생략 가능.

## API Functional Interface

하나의 추상메소드를 가지는 함수적 인터페이스는 익명 객체 구현 시 람다식 이용 가능.

자바에서는 java.util.function 패키지에서 이런 인터페이스 제공.

- Consumer

    매개값 존재, 리턴값 X.

    accept() 메소드 존재.

- Supplier

    매개값 X, 리턴값 존재.

    get(), getAsXX() 메소드 존재.

    ex) get(), getAsInt(), getAsBoolean()

- Function

    매개값 존재, 리턴값 존재. 주로 리턴값으로 Mapping

- Operator

    매개값 존재, 리턴값 존재. 주로 연산 결과를 리턴.

    apply() 시리즈

- Predicate

    매개값 존재, boolean 리턴. 매개값 조사 true/false 리턴.

    test() 시리즈. 

## andThen() / compose()

static, default 메소드와 abstract 메소드는 같지 않음.

따라서 이들이 존재하여도 functional interface 여부에 영향없음.

이러한 default 메소드로 andThen(), compose() 존재.

함수적 인터페이스 연결, 결과값 리턴.

- X.andThen(Y) : X의 결과값으로 Y 인터페이스의 연산을 수행.
- X.compose(Y). Y 결과값을 argument로 X의 연산 수행.

Consumer, Function, Operator 인터페이스의 경우 andThen() 또는 compose() 메소드 제공.