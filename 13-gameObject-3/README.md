## 조건문과 시간

### 1. switch문

- `switch문`은 `(괄호)` 안의 정수에 해당하는 `case` 구문으로 이동하여 프로그램 코드를 실행하는 조건문이다.
- 해당되는 `case`문이 없을 경우 `default` 구문의 코드 블럭을 실행한다.

    ```csharp
    switch(정수)
    {
        case 값:
            코드 블럭
            break;

        default:
            코드 블럭
            break;
    }
    ```

### 2. FPS(Frame Per Second)

- 초당 프레임을 의미하는 것으로 1초에 발생한 업데이트 빈도수를 의미

### 3. Time 클래스

- 유니티에서 제공하는 시간 관련 클래스
- `Time.time` : 실행 시부터 진행한 시간(초 단위)
- `Time.deltaTime` : 이전 프레임이 완료되기까지의 시간(초 단위)
- `Time.timeScale` : 시간 스케일

### 4. Invoke 메소드

- `Invoke(메소드이름, 시간)` : 일정 시간(초) 후에 특정 메소드를 호출
- `InvokeRepeating(메소드이름, 시작시간, 반복 시간간격)` : 시작 시간 후에 반복 간격마다 메소드를 호출

### 5. 씬(Scene) 변환 방법

- `Application.LoadLevel("씬이름")`
- `Application.LoadLevel(씬번호)`
