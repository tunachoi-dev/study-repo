
# 1. 변수의 정의와 역할
변수(**Variable**)는 데이터를 저장하는 **상자(그릇)** 입니다.
이름 그대로 저장된 값이 **변할 수 있는 공간**이라는 뜻을 가지고 있습니다.
- **역할:** 값을 저장해두고 필요할 때 꺼내 사용하는 저장소 역할
- **메모리 접근:** 변수를 선언하면 컴퓨터 메모리 공간을 확보하고, 이름을 통해 해당 공간에 접근할 수 있습니다.
## 기본형 vs 참조형 메모리 저장 방식
- **기본형(Primitive):** 실제 값이 변수에 직접 저장됩니다. (ex. `int`, `double`)
- **참조형(Reference):** 변수에는 **값이 있는 주소(참조값)** 가 저장됩니다. (ex. `String`, 배열, 객체)

---
# 2. 변수 선언, 초기화 및 사용
### 2.1 변수 선언 (Declaration)
```java
int a;      // 정수형 변수 a 선언
int x, y;   // 같은 타입의 변수 여러개 한 번에 선언
```
👉 한 줄에 하나씩 선언하면 가독성이 좋아집니다.
## 2.2 변수 초기화 및 값 대입
- 변수에 처음 값을 저장하는 것을 **초기화(Initialization)** 라고 합니다.
- `=` 기호는 **오른쪽 값을 왼쪽 변수에 저장**한다는 의미입니다.
```java
int b = 2;          // 선언과 동시에 초기화
int c = 3, d = 4;   // 여러 개 초기화
int x, y, z;
x = y = z = 10;     // 여러 변수에 같은 값 할당
```
## 2.3 변수 사용 및 값 변경
```java
int age = 25;
System.out.println(age);  // 25 출력

age = 30;                 // 값 변경
System.out.println(age);  // 30출력
```
👉 변수의 값을 읽는다고 해서 값이 사라지지 않으며, 여러 번 사용할 수 있습니다.
## 2.4 초기화의 중요성 & 변수 종류
자바의 **지역 변수(Local Variable)** 는 선언만으로는 사용이 불가능합니다.
👉**사용 전에 반드시 초기화해야**하며, 초기화하지 않으면 컴파일 에러가 발생합니다.
```java
int num;
System.out.println(num);  // 오류: 초기화되지 않음
```
반면 인스턴스 변수와 클래스 변수는 자동으로 기본값으로 초기화됩니다.

| 종류             | 선언 위치              | 기본값 자동 초기화 | 사용 전 초기화 필요 | 예시                  |
| -------------- | ------------------ | ---------- | ----------- | ------------------- |
| 지역 변수          | 메서드 내부             | X          | O 필요        | `int a = 0;`        |
| 인스턴스 변수        | 클래스 내부(인스턴스 소속)    | O          | X 자동 초기화    | `int count;`        |
| 클래스 변수(static) | 클래스 내부(static 키워드) | O          | X 자동 초기화    | `static int total;` |

---
# 3. 변수 명명 규칙 (Naming Rules)
| 구분       | 규칙 (필수)                   | 관례 (권장)                          |
| -------- | ------------------------- | -------------------------------- |
| 변수 이름    | 숫자로 시작할 수 없음              | camelCase 사용 (예: `studentCount`) |
| 허용 문자    | 영문자, 숫자, `$`, `_`         | 단어 구분 시 첫 글자 대문자                 |
| 공백 및 예약어 | 공백 X, 예약어 X (예: int int;) | -                                |
| 대소문자 구분  | `myVar` ≠ `myvar`         | -                                |
| 시작 문자    | 문자로 시작 필수                 | 상수는 대문자 + `_` (예: `USER_LIMIT`)  |

## 실무에서 자주 보는 변수명 스타일**
### 좋은 예시
- `userId` (사용자 ID)
- `totalPrice` (총 금액)
- `isActive` (활성 여부, boolean은 보통 is/has로 시작)
- `MAX_RETRY_COUNT` (상수, 대문자 + 언더바)
### 나쁜 예시
- `a`, `b`, `temp` (의미 없는 이름)
- `user_id` (스네이크 케이스 X)
- `UserId` (변수는 소문자로 시작해야 함)

---
# 4. 변수의 타입 (Data Types)
## 4.1 기본 데이터 타입 (Primitive Types)
| 타입      | 설명         | 크기    | 실무 사용 예시        | 실무 사용 빈도 |
| ------- | ---------- | ----- | --------------- | -------- |
| int     | 정수         | 4byte | 나이, 개수 등 일반 정수  | 매우 많음    |
| long    | 큰 정수       | 8byte | ID, 타임스탬프 등     | 많음       |
| double  | 실수         | 8byte | 소수점 계산 (기본 실수형) | 많음       |
| float   | 실수         | 4byte | 정밀도 낮음, 잘 안 씀   | 거의 안 씀   |
| boolean | true/false | 1byte | 상태값, 조건문        | 자주 사용    |
| byte    | 작은 정수      | 1byte | 파일 전송, 네트워크     | 특수 용도    |
| short   | 작은 정수      | 2byte | 거의 안 씀          | 거의 안 씀   |
| char    | 문자 1개      | 2byte | 간단한 문자 저장       | 드물게 사용   |
### 금액 계산 주의
`double`은 소수점 계산에서 오차가 발생할 수 있습니다.
실무에서는 **BigDecimal**을 사용합니다.
```java
import java.math.BigDecimal;

public class BigDecimalExample {
	public static void main(String[] args) {
	// double로 계산할 때
	double d1 = 0.1;
	double d2 = 0.2;
	System.out.println("double 계산 결과: " + (d1 + d2));
	// double 계산 결과 : 0.30000000000000004
	
	// BigDecimal로 계산할 때
	BigDecimal b1 = new BigDecimal("0.1");
	BigDecimal b2 = new BigDecimal("0.2");
	BigDecimal result = b1.add(b2);
	
	System.out.println("BigDecimal 계산 결과: " + result);
	// BigDecimal 계산 결과: 0.3
	}
}
```
- `new BigDecimal(0.1)` 처럼 `double`을 직접 넣는 것은 X (이미 오차가 발생함)
- `"0.1"` 처럼 문자열로 넣어야 정확한 값이 저장
- `BigDecimal`은 금액, 금융 계산, 정밀한 수학 연산에 자주 사용
- 덧셈: `add()`, 뺄셈: `subtract()`, 곱셈: `multiply()`, 나눗셈: `divide()` 메서드 사용.
## 4.2 참조 데이터 타입 (Reference Types)
### String의 특별함
```java
String name1 = "tunachoi-dev";              // 문자열 리터럴 (권장)
String name2 = new String("tunachoi-dev");  // 객체 생성 방식
```
- `String`은 참조형이지만 기본형처럼 사용 가능
- 실무에서는 첫 번재 방식을 주로 사용 (메모리 효율적)
## 4.3 리터럴(Literal) 표기법

|타입|예시|설명|
|---|---|---|
|정수|`100`, `0b1010`, `0xFF`|10진수, 2진수, 16진수|
|실수|`3.14`, `3.14f`|double은 기본형, float은 f 필요|
|long|`10000000000L`|끝에 `L` 붙이기|
|문자열|`"Hello"`|큰따옴표 사용|
|문자|`'A'`|작은따옴표 사용|
|불리언|`true`, `false`|논리값|
```java
long bigNum = 1_000_000_000L;    // long 리터럴은 끝에 L
float num = 3.14f;               // float 리터럴은 끝에 f
double pi = 3.14;                // double은 기본형이라 d 생략 가능

int binary = 0b1010;             // 2진수 리터럴
int hex = 0xFF;                  // 16진수 리터럴
int readable = 1_000_000;        // 언더바로 가독성 향상
```
## 4.4 언더스코어(`_`)
**언더스코어(`_`)** 는 Java 7 이상부터 지원되는 숫자 리터럴 구분자입니다.
#### 숫자 리터럴에서 `_`(언더스코어) 사용법
```java
public class UnderscoreExample {
	public static void main(String[] args) {
		long bigNum = 1_000_000_000L;  // 언더스코어로 가독성 향상
		int binary = 0b1010_1100;      // 2진수에도 사용 가능
		int hex = 0xFF_FF;             // 16진수에도 사용 가능
		
		System.out.println(bigNum);    // 1000000000
		System.out.println(binary);    // 172
		System.out.println(hex);       // 65535
	}
}
```
**설명**
- `_`는 **숫자 값을 바꾸지 않으며**, 단순히 사람이 읽기 쉽게 도와주는 역할만 합니다.
- 자릿수를 구분할 때 **숫자 사이**에만 넣을 수 있습니다.
- `1_000_000` -> 올바른 사용
- `_1000000` -> 맨 앞에는 사용 불가
- `1000000_` -> 맨 뒤에도 사용 불가
- `1000_.00` -> 소수점 바로 앞뒤에도 사용 불가
**팁:**
- 큰 숫자(예: ID, 금액, 밀리초 단위 시간 등)를 다룰 때 `_`를 넣으면 코드 가독성이 훨씬 좋아집니다.
- 실제 값에는 전혀 영향을 주지 않기 때문에 안심하고 써도 됩니다.

---
# 5. 상수 (Constants)
값이 바뀌지 않게 하려면 `final` 키워드를 사용합니다.
```java
final int BIRTH_YEAR = 1999;
System.out.println(BIRTH_YEAR);
```
- 변경 불가능(읽기 전용)
- 상수 이름은 **대문자 + `_`** 관례 사용

---
# 6. 문자열 결합 (Concatenation)
`+` 연산자는 문자열 결합 및 수학 연산 두 가지 역할을 합니다.
```java
String name = "tunachoi-dev";
int age = 25;

System.out.println("이름: " + name);
System.out.println("내년 나이: " + (age + 1));
```
**성능 팁**
반복문에서 문자열을 많이 결합할 경우 `StringBuilder`를 사용하세요
```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
	sb.append("데이터").append(i);
}
String result = sb.toString();
```

---
# 7. 실습 예제
```java
public class VariableExmaple {
	public static void main(String[] args) {
		// 1. 사용자 정보
		long userId = 19990209L;
		String username = "tunachoi-dev";
		int age = 27;
		boolean isActive = true;
		
		// 2. 계산 예제
		int currentYear = 2025;
		final int BIRTH_YEAR = 1999;
		int calculatedAge = currentYear - BIRTH_YEAR;
		
		// 3. 출력
		System.out.println("=== 사용자 정보 ===");
		System.out.println("ID: " + userId);
		System.out.println("이름: " + username);
		System.out.println("나이: " + age);
		System.out.println("활성 상태: " + isActive);
		System.out.println("계산된 나이: " + calculatedAge);
		
		// 4. boolean 활용
		if (isActive) {
			System.out.println(username + "님은 활성 사용자입니다.");
		}
	}
}
```
---
# 8. 자주 하는 실수 & 해결법
| 실수 예시                          | 문제 설명     | 해결 방법               |
| ------------------------------ | --------- | ------------------- |
| `System.out.println(userage);` | 변수명 오타    | 선언한 이름과 동일하게 사용     |
| `int num = 3.14;`              | 타입 불일치    | 타입을 맞추거나 캐스팅        |
| `int big = 3000000000;`        | int 범위 초과 | `long` 사용 (`L` 붙이기) |
| `char grade = "A";`            | 큰따옴표는 문자열 | 작은따옴표 사용 `'A'`      |
| 지역 변수 초기화 안 함                  | 컴파일 에러    | 선언 후 값을 먼저 할당       |

---
# 요약 정리
- 변수는 데이터를 저장하고 재사용할 수 있는 공간이다.
- **지역 변수는 반드시 초기화 후 사용**해야 한다.
- 변수는 **명확한 이름 + 타입 선언**으로 가독성을 높인다.
- 실무에서는 `int`, `long`, `double`, `boolean`, `String`이 가장 자주 쓰인다.
- 문자열 결합 시 성능이 중요한 경우 `StringBuilder`를 고려한다.
- 기본형과 참조형은 메모리 저장 방식이 다르다.
- 상수는 `final`로 선언하며 대문자+언더바로 표기한다.
