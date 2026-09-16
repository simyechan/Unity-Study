## Transform과 연산자

### 1. Transform.RotateAround

- 특정 좌표를 기준으로 특정 회전축을 중심으로 회전시키는 메소드이다.
- 다음과 같은 형식으로 사용한다.

    `Transform.RotateAround(Vector3 point, Vector3 axis, float angle);`

### 2. Transform 프로퍼티의 성분 값 수정

- 트랜스폼 프로퍼티의 위치, 회전, 스케일 값은 각 성분의 값을 직접 수정할 수 없다.
- 임시 변수에 저장한 후 성분 값을 수정하고 다시 대입해야 한다.

    `Vector3 tmp = transform.localScale;`
    
    `tmp.x = 2;`
    
    `tmp.y = 2;`
    
    `tmp.z = 2;`
    
    `transform.localScale = tmp;`

### 3. Debug.DrawLine

- 씬 뷰에서 시작점을 기준으로 끝점을 향하는 선을 그리는 메소드이다.
- 다음과 같은 형식으로 사용한다.

    `Debug.DrawLine(시작점, 끝점);`

### 4. 증감 연산자

- 값을 1씩 증가하거나 감소시키는 연산자이다.
- 증가 연산자 `++`
- 감소 연산자 `--`

### 5. 대입 연산자

#### 1. 단순 대입 `=`

- 우항의 값을 좌항에 대입하는 연산자이다.

#### 2. 복합 대입 `+=`, `-=`, `*=`, `/=`, `%=`

- 좌항과 우항의 값을 더하거나 빼는 등의 연산을 수행한 후 그 결과를 좌항에 대입한다.
