# Kotlin 문법 - 코루틴 기초 (Coroutine 소개)

## 학습 요약

- **코루틴(Coroutine)**
    - 비동기 작업을 간단하게 처리할 수 있도록 돕는 경량 스레드
    - 수천 개를 동시에 실행해도 스레드보다 부담이 적음
- **`suspend` 함수**
    - *일시 중단 가능한 함수*
    - 다른 `suspend` 함수나 코루틴 안에서만 호출 가능
    - 메인 스레드를 차단하지 않고, 비동기적으로 실행 가능
- **CoroutineScope**
    - 코루틴이 실행되는 범위를 정의
    - `GlobalScope`, `lifecycleScope`, `viewModelScope` 등이 있음
- **lifecycleScope**
    - 안드로이드 **LifecycleOwner(Activity, Fragment)**와 연결된 Scope
    - Lifecycle 상태(`onDestroy`)에 맞춰 자동으로 코루틴이 취소됨 → 메모리 누수 방지
- **launch vs async**
    - `launch` : 반환값 없는 코루틴 실행
    - `async` : 값을 반환(`Deferred<T>`)하는 코루틴 실행 → `await()` 필요

---

## 실습 코드

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // lifecycleScope : 액티비티 라이프사이클에 맞춰 코루틴 실행
        lifecycleScope.launch {
            myFunc(10) {
                println("콜백 실행")
            }
        }

        // async 사용 예제
        lifecycleScope.launch {
            val result = async {
                heavyTask()
            }.await()
            println("async 결과: $result")
        }
    }
}

// suspend 함수: 코루틴 안에서만 호출 가능
suspend fun myFunc(a: Int, callBack: () -> Unit = {}) {
    println("함수 시작: $a")
    callBack()
    println("함수 끝!!")
}

// 시간이 오래 걸리는 작업 흉내
suspend fun heavyTask(): String {
    delay(2000) // 2초 지연 (비동기)
    return "작업 완료!"
}

```

---

## 추가 정리 포인트

- **`delay(ms)`** : Thread.sleep()과 달리 스레드를 차단하지 않고 코루틴만 일시 중단
- **코루틴 컨텍스트 (Dispatcher)**
    - `Dispatchers.Main` : UI 업데이트용
    - `Dispatchers.IO` : 네트워크/DB 작업용
    - `Dispatchers.Default` : CPU 연산용
- 안드로이드에서는 `lifecycleScope`, `viewModelScope`를 사용하면 안전하게 코루틴 관리 가능

# Kotlin 코루틴 빌더/컨텍스트 정리

| 키워드 | 반환값 | 특징 | 사용 예시 |
| --- | --- | --- | --- |
| **launch** | `Job` | - 결과값 없음- fire-and-forget 방식- 실패 시 예외 발생하면 상위로 전파 | `lifecycleScope.launch { ... }` |
| **async** | `Deferred<T>` | - 값을 반환할 수 있음- `await()`로 결과 가져옴- 여러 비동기 작업 동시 실행 후 결과 합칠 때 유용 | `val result = async { heavyTask() }.await()` |
| **withContext** | `T` (직접 반환) | - 특정 `Dispatcher`로 컨텍스트 전환- 블록 실행 후 결과 바로 반환- 구조적으로 안전 (취소/예외 전파) | `val text = withContext(Dispatchers.IO) { loadFile() }` |

---

## 간단 예시

```kotlin
lifecycleScope.launch {
    // launch: 반환값 없음
    launch {
        println("launch 실행")
    }

    // async: 결과값 await()
    val result = async {
        delay(1000)
        "작업 완료"
    }.await()
    println(result)

    // withContext: dispatcher 변경 + 결과 즉시 반환
    val ioResult = withContext(Dispatchers.IO) {
        "IO 작업 완료"
    }
    println(ioResult)
}

```

---
