# Kotlin 기초 문법 복습 – 간단한 계산기 만들기

## 📌 학습 목적

- 변수, 자료형, 입력/출력 문법 복습
- `when` 조건문 활용
- 기본 예외 처리(`toDoubleOrNull()`)

## 💡 구현 아이디어

1. 사용자에게 두 숫자와 연산자 입력 받기
2. 숫자는 `Double` 타입으로 변환
3. 연산자는 `when` 구문으로 처리
4. 나눗셈 예외 처리(0으로 나누는 경우 방지)

## 💻 코드 예시

```kotlin

fun main() {
    print("첫 번째 숫자를 입력하세요: ")
    val num1 = readLine()?.toDoubleOrNull() ?: 0.0

    print("연산자를 입력하세요 (+, -, *, /): ")
    val op = readLine()

    print("두 번째 숫자를 입력하세요: ")
    val num2 = readLine()?.toDoubleOrNull() ?: 0.0

    val result = when (op) {
        "+" -> num1 + num2
        "-" -> num1 - num2
        "*" -> num1 * num2
        "/" -> if (num2 != 0.0) num1 / num2 else "0으로 나눌 수 없습니다."
        else -> "잘못된 연산자입니다."
    }

    println("결과: $result")
}

```

## 📝 실행 예시

```makefile

첫 번째 숫자를 입력하세요: 10
연산자를 입력하세요 (+, -, *, /): *
두 번째 숫자를 입력하세요: 3
결과: 30.0

```

## 📎 Tip

- `readLine()`은 문자열로 입력을 받으니 형변환이 필요
- `toDoubleOrNull()`을 사용하면 잘못된 입력 시 예외를 막고 기본값 설정 가능
