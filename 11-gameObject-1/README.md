## Vector3와 생명주기

### 1. Vector3.Angle

- 매개변수로 전달된 두 벡터의 각도를 계산하는 메소드이다.
- 다음과 같은 형식으로 사용한다.

    `Vector3.Angle(Vector3 from, Vector3 to);`

### 2. Vector3.Distance

- 매개변수로 전달된 두 벡터의 거리를 계산하는 메소드이다.
- 다음과 같은 형식으로 사용한다.

    `Vector3.Distance(Vector3 a, Vector3 b);`

### 3. OnEnable() 메소드

- 게임 시작 이후, 첫 프레임 시작 전, 게임 오브젝트 또는 컴포넌트가 활성화될 때(켜질 때) 호출되는 함수이다.

### 4. OnDisable() 메소드

- 게임 오브젝트 또는 컴포넌트가 비활성화될 때(꺼질 때)마다 호출되는 함수이다.

### 5. 게임 오브젝트 비활성화 / 활성화

- `GameObject.SetActive(true or false);`

### 6. 컴포넌트 비활성화 / 활성화

- `컴포넌트.enabled = true or false;`
