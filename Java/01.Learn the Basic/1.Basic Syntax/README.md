# Basic Syntax

---
## 목차
1. [자바 프로그램의 기본 구조](#1-자바-프로그램의-기본-구조)
2. [명명 규칙 (Naming Conventions)](#2-명명-규칙-naming-conventions)
3. [예약어 (Reserved Keywords)](#3-예약어-reserved-keywords)
4. [주석 (Comments)](#4-주석-comments)
5. [표현식과 문 (Expressions & Statements)](#5-표현식과-문-expressions--statements)
6. [형변환 (Type Casting)](#6-형변환-type-casting)
7. [출력 (Output)](#7-출력-output)
8. [입력 (Input)](#8-입력-input)
9. [패키지 (Packages)](#9-패키지-packages)
10. [배열 (Arrays) - 데이터 구조 기초](#10-배열-arrays---데이터-구조-기초)
11. [객체 지향 프로그래밍 (OOP) 입문](#11-객체-지향-프로그래밍-oop-입문)
12. [학습 체크리스트](#학습-체크리스트-)

---
## 1. 자바 프로그램의 기본 구조
자바 프로그램은 **최소 하나 이상의 클래스**를 포함해야 합니다.
```java
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hello, World!");
	}
}
```
### 핵심 개념
#### 클래스 (Class)
- 관련된 메서드들을 담는 컨테이너
- `class` 키워드로 정의
- 클래스명과 파일명이 일치해야 함
#### 메서드 (Method)
- 특정 작업을 수행하는 코드 블록
- 클래스에 속한 함수를 메서드라고 부름
#### Main 메서드
- 모든 자바 프로그램의 시작점 (진입점, Entry Point)
- `public static void main(String[] args)` 형태로 선언
	- `void`: 반환값이 없음
	- `static`: 객체 생성 없이 호출 가능한 정적 메서드
#### 코드 작성 규칙
- 코드 블록은 중괄호 `{}`로 감싸기
- 모든 문장은 세미콜론 `;`으로 끝내기
- 들여쓰기로 코드 가독성 높이기

---
## 2. 명명 규칙 (Naming Conventions)
자바에서 변수, 클래스, 메서드 등에 부여하는 이름을 **식별자(Identifier)** 라고 합니다.
### 기본 규칙
#### 사용 가능한 문자
- 문자, 숫자, 밑줄(`_`), 달러 기호(`$`)
#### 제약 사항
- 반드시 문자로 시작 (숫자로 시작 불가)
- 예약어 사용 불가
- 대소문자 구분(`myVar` ≠ `myvar`)
### 명명 스타일
| 대상         | 규칙                                 | 예시                                         |
| ---------- | ---------------------------------- | ------------------------------------------ |
| **클래스**    | 파스칼 표기법<br>모든 단어의 첫 글자 대문자         | `Person`, `OrderDetail`, `UserService`     |
| **변수/메서드** | 카멜 표기법<br>첫 단어 소문자, 이후 단어 첫 글자 대문자 | `firstName`, `calculateSum`, `getUserInfo` |
| **상수**     | 대문자 + 언더스코어                        | `MAX_COUNT`, `DB_URL`, `BIRTH_YEAR`        |
| **패키지**    | 모두 소문자                             | `com.example.demo`, `org.springframework`  |
**팁:** Spring 프로젝트에서는 일관된 명명 규칙이 필수입니다. Controller, Service, Repository 등 게층별로 명확한 네이밍을 사용하세요.

---
## 3. 예약어 (Reserved Keywords)
자바에서 특별한 의미로 미리 정의된 단어들로, **변수/클래스/메서드 이름으로 사용할 수 없습니다.**
### 주요 예약어
**데이터 타입**
- `int`, `long`, `double`, `boolean`, `char`, `float`, `byte`. `short`
**접근 제어자**
- `public`, `private`, `protected`
**클래스 관련**
- `class`, `interface`, `extends`, `implements`
**메서드 관련**
- `static`, `void`, `return`
**제어문**
- `if`, `else`, `for`, `while`, `switch`, `case`, `break`, `continue`
**예외 처리**
- `try`, `catch`, `finally`, `throw`, `throws`
**기타**
- `new`, `this`, `super`, `final`, `package`, `import`, `true`, `false`, `null`

---
## 4. 주석 (Comments)
코드에 설명을 추가하거나 특정 코드를 실행되지 않도록 할 때 사용합니다.
```java
// 한 줄 주석
// 이 줄은 실행되지 않습니다.

/*
	여러 줄 주석
	여러 줄에 걸쳐
	설명을 작성할 수 있습니다.
*/

/**
	* JavaDoc 주석 - API 문서 생성용
	* 
	* @param name 사용자 이름
	* @return 인사 메시지
	*/
	public String greet(String name) {
		return "Hello, " + name;
	}
```
**팁:** JavaDoc 주석은 Swagger와 함께 사용하여 API 문서를 자동 생성할 수 있습니다.

---
## 5.표현식과 문 (Expressions & Statements)
### 문장 (Statement)
실행 가능한 완전한 코드 단위로, **세미콜론(`;`)으로 끝납니다.**
```java
int x = 5;                   // 선언문
System.out.println("Hi");    // 출력문
if (x > 3) {...}             // 제어문
```
### 표현식 (Expression)
**값을 반환하는** 코드 조각
```java
5 + 3              // 8을 반환
x > 10             // true 또는 false 반환
"Hello" + "World"  // "HelloWorld" 반환
```
### 연산자 우선 순위
1. **괄호** `()` - 가장 높은 우선순위
2. **곱셈/나눗셈 `*`, `/`** - 덧셈/뺄셈보다 먼저
3. **덧셈/뺄셈 `+`, `-`**
4. **대입 연산자 `=`** - 가장 낮은 우선순위
```java
int result = 10 + 5 * 2;      // 20 (곱셈 먼저)
int result = (10 + 5) * 2;    // 30 (괄호 먼저)
```
**팁:** 가독성을 위해 괄호를 적극 활용하세요!

---
## 6. 형변환 (Type Casting)
변수나 표현식의 타입을 변경하는 것을 형변환이라고 합니다.
### 자동(묵시적) 형변환
작은 타입 -> 큰타입으로 자동 변환 (데이터 손실 없음)
```java
int num = 100;
long bigNum = num;        // int -> long 자동 변환
double dicimal = bigNum;  // long -> double 자동 변환

// 순서: byte < short < int < long < float < double
```
### 명시적 형변환
큰 타입 -> 작은 타입으로 변환 시 **(타입)** 형태로 명시해야 함
```java
double decimal = 9.78;
int num = (int) decimal;  // 9 (소수점 버림)

long bigNum = 1000L;
int smallNum = (int) bigNum;  // 명시적 변환 필요
```
**주의:** 명시적 형변환 시 데이터 손실이나 오버플로우가 발생할 수 있습니다.

---
## 7. 출력 (Output)
콘솔에 값을 출력할 때 `System.out` 클래스를 사용합니다.
```java
// 줄바꿈 포함 출력
System.out.println("Hello, World!");
System.out.println("다음 줄로 이동합니다.");

// 줄바꿈 없이 출력
System.out.print("안녕");
System.out.print("하세요");  // 출력: 안녕하세요

// 형식 지정 출력
System.out.printf("나이: %d세, 이름: %s", 27, "tunachoi-dev");
```
### 문자열 연결 (String Concatenation)
`+` 연산자로 문자열과 변수를 결합할 수 있습니다.
```java
String name = "tunachoi-dev";
int age = 27;

System.out.println("이름: " + name + ", 나이: " + age);
// 출력: 이름: tunachoi-dev, 나이: 27

// 숫자는 자동으로 문자열로 변환됨
System.out.println("100" + 200);  // "100200" (문자열)
System.out.println(100 + 200);    // 300 (숫자)
```
**팁:** 개발 중에서는 `System.out.println()`으로 디버깅하지만, 실무에서는 로깅 라이브러리(Logback, SLF4J)를 사용합니다.

---
## 8. 입력 (Input)
사용자로부터 입력을 받을 때 `Scanner` 클래스를 사용합니다.
### Scanner 사용법
```java
import java.util.Scanner;

public class InputExample {
	public static void main(String[] args) {
	// 1. Scanner 객체 생성
	Scanner scanner = new Scanner(System.in);
	
	// 2. 문자열 입력
	System.out.print("이름을 입력하세요: ");
	String name = scanner.nextLine();
	
	// 3. 정수 입력
	System.out.print("나이를 입력하세요: ");
	int age = scanner.nextInt();
	
	// 4. 실수 입력
	System.out.print("키를 입력하세요: ");
	double height = scanner.nextDouble();
	
	System.out.println("이름: " + name + ", 나이: " + age + ", 키: " + height);
	}
}
```
#### 주요 메서드
| **메서드**        | **설명**         | **예시**           |
| -------------- | -------------- | ---------------- |
| `nextLine()`   | 문자열 입력 (공백 포함) | `"tunachoi-dev"` |
| `next()`       | 단어 입력 (공백 제외)  | `"Hello"`        |
| `nextInt()`    | 정수 입력          | `27`             |
| `nextDouble()` | 실수 입력          | `3.14`           |
**주의:** 입력 타입과 메서드가 일치하지 않으면 `InputMismatchException`오류가 발생합니다
### BufferedReader(성능이 중요할 때)
```java
import java.io.*;

BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String input = br.readLine();  // 문자열로 입력받음
int number = Integer.parseInt(input);  // 정수로 변환
```
**팁:** Spring에서는 HTTP 요청(`@RequestParam`, `@RequestBody`)으로 사용자 입력을 받습니다.

---
## 9. 패키지 (Packages)
관련된 클래스들을 묶어주는 폴더 구조입니다.
### 패키지 선언과 가져오기
```java
// 파일 맨 위에 패키지 선언
package com.example.demo.controller;

// 다른 패키지의 클래스 가져오기
import java.util.Scanner;
import java.util.List;
import com.example.demo.service.UserService;
```
#### 패키지 명명 규칙
- **모두 소문자** 사용
- 회사 도메인을 역순으로 사용
	- 예시: `com.example.demo`, `org.springframework.boot`
#### Spring 프로젝트의 전형적인 패키지 구조
```
com.example.demo
├── controller (HTTP 요청 처리)
├── service (비즈니스 로직)
├── repository (데이터베이스 접근)
├── dto (데이터 전송 객체)
├── entity (데이터베이스 테이블 매핑)
└── config (설정 파일)
```
**팁:** 패키지 구조를 명확히 하면 코드 관리와 팀 협업이 훨씬 수월합니다.

---
## 10. 배열(Arrays) - 데이터 구조 기초
같은 타입의 여러 값을 하나의 변수에 저장하는 자료구조입니다.
### 배열 선언과 생성
```java
// 방법 1: 선언 후 생성
int[] numbers = new int[5];  // 크기 5인 배열 생성

// 방법 2: 선언과 동시에 초기화
int[] numbers = {1, 2, 3, 4, 5};

// 방법 3: 선언, 생성, 초기화 분리
int[] numbers;
numbers = new int[5];
numbers[0] = 10;
```
### 배열 사용
```java
// 배열 요소 접근 (인덱스는 0부터 시작)
int[] scores = {90, 85, 88, 92, 95};
System.out.println(scores[0]);  // 90
System.out.println(scores[4]);  // 95

// 배열 길이
System.out.println(scores.length);  // 5

// 배열 요소 수정
scores[1] = 100;
```
### 배열 순회
```java
int[] numbers = {1, 2, 3, 4, 5};

// 일반 for문
for (int i = 0; i < numbers.length; i++) {
	System.out.println(numbers[i]);
}

// 향상된 for문 (for-each)
for (int num : numbers) {
	System.out.println(num);
}
```
### 2차원 배열
```java
// 2차원 배열 선언
int[][] matrix = new int[3][4];  // 3행 4열

// 초기화
int[][] matrix = {
	{1, 2, 3},
	{4, 5, 6},
	{7, 8, 9}
};

// 접근
System.out.println(matrix[0][1]);  // 2 (0행 1열)
```
**주의:** 배열은 한 번 생성되면 크기를 변경할 수 없습니다.
**팁:** Spring에서 여러 데이터를 조회할 때 `List<User>` 형태로 반환합니다.

---
## 11. 객체 지향 프로그래밍 (OOP) 입문
자바는 객체 지향 언어이며, Spring도 객체 지향으로 설계되어 있습니다.
### 클래스와 객체
**클래스(Class):** 객체를 만들기 위한 설계도 (Blueprint)
**객체(Object):** 클래스로 만들어진 실체 (Instance)
```java
// 클래스 정의
public class User{
	// 필드 (속성)
	String name;
	int age;
	
	// 메서드 (동작)
	public void introduce() {
		System.out.println("제 이름은" + name + "이고, " + age + "세입니다.");
	}
}

// 객체 생성 및 사용
User user = new User();
user.name = "tunachoi-dev";
user.age = 27;
user.introduce();  // 출력: 제 이름은 tunachoi-dev고, 27세입니다.
```
### 기본형 vs 참조형
| **구분**     | **기본형(Primitive)**         | **참조형(Reference)**    |
| ---------- | -------------------------- | --------------------- |
| **저장 값**   | 실제 값 자체                    | 객체의 주소(참조)            |
| **메모리 할당** | 선언 시 자동 할당                 | `new` 연산자로 할당         |
| **복사 방식**  | 값 복사(독립적)                  | 참조 복사 (연결됨)           |
| **예시**     | `int`, `double`, `boolean` | `String`, `배열`, 모든 객체 |
```java
// 기본형 - 값 복사
int a = 10;
int b = a;
b = 20;
System.out.println(a);  // 10 (변경 안 됨)

// 참조형 - 참조 복사
int[] arr1 = {1, 2, 3};
int[] arr2 = arr1;
arr2[0] = 100;
System.out.println(arr1[0]);  // 100 (변경됨!)
```
### 메서드 (Methods)
특정 작업을 수행하는 코드를 캡슐화하여 재사용할 수 있게 합니다.
```java
public class Calculater {
	// 메서드 정의
	public int add(int a, int b) {
		return a + b;
	}
	
	// 메서드 오버로딩 - 같은 이름, 다른 매개변수
	public double add(double a, double b) {
		return a + b;
	}
	
	public int add(int a, int b, int c) {
		return a + b + c;
	}
}

// 메서드 호출
Calculator calc = new Calculater();
System.out.println(calc.add(5, 3));
System.out.println(calc.add(5.5, 3.2));
System.out.println(calc.add(1, 2, 3));
```
**메서드 시그니처 = 메서드 이름 + 매개변수 타입 (순서 포함)**
**주의:** 반환 타입만 다른 것은 오버로딩이 아닙니다.
**실무 팁:** Spring의 Controller, Service, Repository는 모두 클래스로 만들어진 객체들입니다.
