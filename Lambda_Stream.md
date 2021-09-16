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

 

위의 코드에서 1~3은 기능적으로 동일.

변수 타입은 자동으로 인식 가능하므로 1에서 2처럼 생략이 가능하고, 실행문이 하나일 경우에는 2에서 3처럼 braces{ }  생략이 가능.

결과값 반환이 필요한 경우 명시하여 4의 형태로 기술 가능.

{ }안에 return 코드만이 존재할 경우에 다시 5의 형태로 생략 가능.

~ 작성 중 ~