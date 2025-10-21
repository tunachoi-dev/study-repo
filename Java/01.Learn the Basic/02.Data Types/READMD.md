# Data Types
## 목차
1. [데이터 타입이란?](#1-데이터-타입이란)
2. [기본 데이터 타입 (Primitive Data Types)](#2-기본-데이터-타입-primitive-data-types)
3. [비기본 데이터 타입 (Non-Primitive Data Types)](#3-비기본-데이터-타입-non-primitive-data-types)
4. [기본형 vs 참조형 비교](#4-기본형-vs-참조형-비교)
5. [상수 (Constants)](#5-상수-constants)
6. [실무 팁](#6-실무-팁)
## 1. 데이터 타입이란?
자바에서 **변수는 반드시 특정 데이터 타입으로 지정**되어야 합니다. 데이터 타입은 변수가 어떤 종류의 값을 담을 수 있는지, 그리고 얼마나 많은 메모리를 사용할지를 결정합니다.
### 데이터 타입의 분류
자바의 데이터 타입은 크게 두 그룹으로 나뉩니다.
```
데이터 타입
├── 기본 데이터 타입 (Primitive Data Types) - 8가지
│   ├── 정수형: byte, short, int, long
│   ├── 실수형: float, double
│   ├── 문자형: char
│   └── 논리형: boolean
│
└── 비기본 데이터 타입 (Non-Primitive Data Types / 참조형)
    ├── String
    ├── Array (배열)
    └── Classes (클래스)
```

---
## 2. 기본 데이터 타입 (Primitive Data Types)
기본 데이터 타입은 **실제 값 자체**를 저장하며, 자바에는 총 **8가지**가 있습니다.
### 2-1. 정수형 (Integer Types)
정수 값을 저장하는 타입입니다.

| 타입      | 메모리 크기           | 범위               | 설명                        |
| ------- | ---------------- | ---------------- | ------------------------- |
| `byte`  | 1 byte (8 bits)  | -128 ~ 127       | 메모리 절약용, 파일 전송 등에 사용      |
| `short` | 2 byte (16 bits) | -32.768 ~ 32.767 |                           |
| `int`   | 4 byte (32 bits) | 약 -21억 ~ 21억     | **가장 많이 사용**하는 정수 타입      |
| `long`  | 8 byte (64 bits) | 약 -922경 ~ 922경   | 큰 정수 저장 시 사용. 값 끝에 `L` 필수 |
#### 코드 예제
```java
byte smallNumber = 127;
short mediumNumber = 32000;
int standardNumber = 21000000;         // 가장 많이 사용
long bigNumber = 9223213213432532532431L;  // L 또는 l 필수
```
**팁:** 정수는 기본적으로 `int`를 사용하고, `int` 범위를 벗어나는 큰 숫자만 `long`을 사용하세요.
### 2-2. 실수형 (Floating-Point Types)
소수점이 있는 실수 값을 저장하는 타입입니다.

| 타입       | 메모리 크기  | 정밀도         | 설명                   |
| -------- | ------- | ----------- | -------------------- |
| `float`  | 4 bytes | 소수점 6~7자리   | 값 끝에 `f` 필수          |
| `double` | 8 bytes | 소수점 15~16자리 | **가장 많이 사용**하는 실수 타입 |
#### 코드 예제
```java
float price = 19.99f;            // f 또는 F 필수
double pi = 3.141592653589793;   // 기본 실수 타입

// 과학적 표기법 (Scientific notation)
double scientificNum1 = 3.5e3;  // 3.5 x 10^3 = 3500.0
double scientificNum2 = 1.2e-4; // 1.2 x 10^-4 = 0.00012
```
**팁:** 실수는 기본적으로 `double`을 사용하세요. `float`는 메모리 절약이 중요할 때만 사용합니다.
### 2-3. 문자형 (Character Type)
단일 문자를 저장하는 타입입니다.

| 타입     | 메모리 크기  | 설명                                      |
| ------ | ------- | --------------------------------------- |
| `char` | 2 bytes | 단일 문자 또는 유니코드 값 저장. **작은 따옴표 `' '` 사용** |
#### 코드 예제
```java
char grade = 'A';
char korean = '가';
char symbol = '$';

// 유니코드 표현
char unicode = '\u0041';  // 'A'와 동일

// ASCII 값으로 표현
char letter = 65;         // 'A'와 동일
```
### 2-4. 논리형 (Boolean Type)
참(`true`) 또는 거짓(`false`) 값만 저장하는 타입입니다.

| 타입        | 메모리 크기 | 값                 | 설명          |
| --------- | ------ | ----------------- | ----------- |
| `boolean` | 1 byte | `true` 또는 `false` | 조건문에서 주로 사용 |
#### 코드 예제
```java
boolean isStudent = true;
boolean isAdult = false;

// 조건문에서 사용
if (isStudent) {
	System.out.println("학생입니다.");
}
```
### 2-5. 기본형 타입 정리표
| 분류      | 타입        | 크기      | 범위               | 기본값      | 자주 사용 |
| ------- | --------- | ------- | ---------------- | -------- | ----- |
| 정수형     | `byte`    | 1 bytes | -128 ~ 127       | `0`      | ❌     |
|         | `short`   | 2 bytes | -32,768 ~ 32.767 | `0`      | ❌     |
|         | `int`     | 4 bytes | 약 -21억 ~ 21억     | `0`      | ⭐     |
|         | `long`    | 8 bytes | 약 -922경 ~ 922경   | `0L`     | ⭐     |
| **실수형** | `float`   | 4 bytes | 6~7자리 소수점        | `0.0f`   | ❌     |
|         | `double`  | 8 bytes | 15~16자리 소수점      | `0.0`    | ⭐     |
| **문자형** | `char`    | 2 bytes | 0 ~ 65,535(유니코드) | `\u0000` | ⚠️    |
| **논리형** | `boolean` | 1 byte  | true/false       | `false`  | ⭐     |
**실무에서 자주 사용하는 타입:** `int`, `long`, `double`, `boolean`

---
## 3. 비기본 데이터 타입 (Non-Primitive Data Types)
비기본 데이터 타입은 **참조 타입(Reference Types)** 이라고도 불리며, **객체의 메모리 주소(참조)** 를 저장합니다.
### 3-1. 비기본 타입의 종류
| 타입                | 설명          | 특징                           |
| ----------------- | ----------- | ---------------------------- |
| **String**        | 문자열(텍스트) 저장 | 큰따옴표 `" "`사용. 가장 많이 사용하는 참조형 |
| **Array (배열)**    | 여러 값을 저장    | 대괄호 `[]` 사용                  |
| **Classes (클래스)** | 객체 생성 템플릿   | 사용자가 정의하거나 제공된 클래스 사용        |
### 3-2. String (문자열)
**String**은 문자의 시퀀스(문자열)을 저장하는 참조형 타입입니다.
#### 특징
- 큰따옴표 `" "`로 둘러싸야 함
- 자바에서 가장 많이 사용되는 타입
- 객체지만 특별한 대우를 받음 (`new` 없이도 생성 가능)
#### 코드 예제
```java
// String 생성 방법 1: 리터럴 (권장)
String name = "tunachoi-dev";
String message = "Hello, Java!";

// String 생성 방법 2: new 키워드
String greeting = new String("안녕하세요");

// String 연결
String fullName = "tunachoi-" + "dev";    // "tunachoi-dev"
String info = "이름: " + name;            // "이름: tunachoi-dev";

// 주요 String 메서드
System.out.println(name.length());            // 12 (길이)
System.out.println(message.toUpperCase());    // "HELLO, JAVA!"
System.out.println(message.toLowerCase());    // "hello, java!"
System.out.println(message.contains("Java")); // true
```

### 3-3. Array (배열)
**배열**은 같은 타입의 여러 값을 하나의 변수에 저장할 수 있습니다.
#### 코드 예제
```java
// 배열 선언 및 초기화
int[] numbers = {1, 2, 3, 4, 5};
String[] names = {"홍길동", "김철수", "이영희"};

// 배열 접근
System.out.println(numbers[0])    // 1
System.out.println(names[1]);      // "김철수"

// 배열 길
System.out.println(numbers.length);  // 5
```
### 3-4. Classes (클래스)
**클래스**는 객체를 생성하기 위한 템플릿입니다.
#### 코드 예제
```java
// Date 클래스 사용 예
import java.util.Date;

Date today = new Date();
System.out.println(today);  // 현재 날짜와 시간 출력
```
### 3-5. 비기본 타입의 특징
#### 1. 객체 지향
- 객체를 참조하며, 메서드를 호출할 수 있습니다.
- 예: `String`의 `length()`, `toUpperCase()` 등
#### 2. 대문자로 시작
- 일반적으로 대문자로 시작합니다. (예: `String`, `Date`)
#### 3. null 값 가능
- 값을 할당하지 않으면 `null`입니다.
```java
String name;
System.out.println(name);    // 컴파일 오류! (초기화 안 됨)

String name2 = null;
System.out.println(name2);   // null 출력
```
#### 4. new 키워드 사용
- 일반적으로 `new` 키워드로 메모리를 할당합니다.
- `String`과 배열은 예외적으로 축약 표현 가능
```java
// 일반적인 객체 생성
Date today = new Date();

// String은 축약 가능
String name = "tunachoi-dev";    // new String("tunachoi-dev")과 동일
```
#### 5. 참조값 저장
- 변수에는 실제 값이 아닌 **메모리 주소(참조)**가 저장됩니다.
```java
String str1 = "Hello";
String str2 = str1;    // str2는 str1과 같은 주소를 참조

System.out.println(str1 == str2);  // true (같은 주소)
```

---
## 4. 기본형 vs 참조형 비교
| 구분          | 기본형(Primitive)             | 참조형(Reference)              |
| ----------- | -------------------------- | --------------------------- |
| **저장 값**    | 실제 값 자체                    | 객체의 메모리 주소(참조)              |
| **메모리 할당**  | 선언 시 자동 할당                 | `new` 키워드로 할당(String/배열 예외) |
| **표기법**     | 소문자로 시작                    | 대문자로 시작                     |
| **기본값**     | `0`, `false`, `\u0000` 등   | `null`                      |
| **메서드 호출**  | 불가능                        | 가능                          |
| **null 할당** | 불가능                        | 가능                          |
| **예시**      | `int`, `double`, `boolean` | `String`, `Array`, `Date`   |
#### 코드 비교
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
System.out.println(arr1[0]);  // 100 (변경됨)
```

---
## 5. 상수 (Constants)
**상수**는 값이 변경되지 않는 변수입니다. `final` 키워드를 사용하여 선언합니다.
### 5-1. 상수 선언
```java
final int BIRTH_YEAR = 1999;
final double PI = 3.141592;
final String MY_NAME = "tunachoi-dev";
```
### 5-2. 상수의 특징
#### 1. 변경 불가능
```java
final int MAX_COUNT = 100;
MAX_COUNT = 200;    // 컴파일 오류. 상수는 변경 불가
```
#### 2. 명명 규칙
- **모두 대문자**로 작성
- 단어 구분은 **언더스코어(`_`)** 사용
```java
final int MAX_COUNT = 100;
final double TAX_RATE = 0.1;
final String DB_URL = "localhost:3306";
```
#### 3. 초기화 필수
```java
final int NUMBER;  // 컴파일 오류. 초기화 필요
NUMBER = 10;       // 여기서 초기화는 불가능

// 올바른 방법
final int NUMBER = 10;
```
### 5-3. 상수 사용의 장점
#### 1. 가독성 향상
```java
// 나쁜 예
if (age >= 18) {...}

// 좋은 예
final int ADULT_AGE = 18;
if (age >= ADULT_AGE) {...}
```
#### 2. 유지보수 편리
```java
// 값을 한 곳에서만 변경하면 됨
final double TAX_RATE = 0.1;

double price1 = 1000 * (1 + TAX_RATE);
double price2 = 2000 * (1 + TAX_RATE);
double price3 = 3000 * (1 + TAX_RATE);
```
#### 3. 실수 방지
```java
final int MAX_ATTEMPTS = 3;
for (int i = 0; i < MAX_ATTEMPTS; i++) {
	// MAX_ATTEMPTS를 실수로 변경할 수 없음
}
```

---
## 6. 실무 팁
### 6-1. 타입 선택 가이드
| 상황    | 추천 타입     | 이유               |
| ----- | --------- | ---------------- |
| 정수 저장 | `int`     | 가장 기본적이고 성능이 좋음  |
| 큰 정수  | `long`    | `int` 범위를 벗어날 때  |
| 실수 저장 | `double`  | 정밀도가 높고 기본 실수 타입 |
| 참/거짓  | `boolean` | 조건문, 플래그 변수      |
| 문자열   | `String`  | 텍스트 데이터          |
| 단일 문자 | `char`    | 거의 사용 안 함        |
### 6-2. 실무에서 자주 사용하는 타입
#### Spring 백엔드 개발에서 주로 사용
```java
// 사용자 DTO
public class UserDto{
	private long id;            // 데이터베이스 ID
	private String name;        // 이름
	private int age;            // 나이
	private double height;      // 키
	private boolean isActive;   // 활성 상태
}
```
### 6-3. 흔한 실수와 해결법
#### 1. String 비교 시 `==` 사용 X
```java
// 잘못된 방법
String name1 = "tunachoi-dev";
String name2 = "tunachoi-dev";
if (name1 == name2) {...}  // 주소를 비교함

// 올바른 방법
if (name1.equals(name2)) {...} // 값을 비교함
```
#### 2. long 타입에 `L` 미표기
```java
long bigNum = 300000000000;   // 컴파일 오류
long bigNum = 300000000000L;  // 올바름
```
#### 3. float 타입에 `f` 미표기
```java
float price = 19.99;    // 컴파일 오류
float price = 19.99f;   // 올바름
```
#### 4. 정수 나눗셈 주의
```java
int a = 5;
int b = 2;
double result = a / b;
System.out.println(result);    // 2.0 (2.5가 아님)

// 올바른 방법
double result = (double) a / b;  // 2.5
```
#### 5. 실수 계산의 오차
```java
double a = 0.1;
double b = 0.2;
System.out.println(a + b);  // 0.30000000000000004 (오차 발생)

// 금액 계산 시 BigDecimal 사용 권장
```
### 6-4. 성능 고려사항
#### 1. 적절한 타입 크기 선택
```java
// 나쁜 예: 불필요하게 큰 타입
long age = 25L;      // 나이는 int로 충분

// 좋은 예
int age = 25
```
#### 2. 기본형 vs 참조형
```java
// 기본형이 참조형보다 빠름
int count = 0;        // 빠름
Integer count = 0;    // 느림 (객체 생성 오버헤드)
```
