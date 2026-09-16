## Unity 주요 함수

### 1. GetComponent 함수

- 게임 오브젝트에 추가되어 있는 컴포넌트를 가져오는 메소드이다.
- 다음과 같은 형식으로 사용한다.

    GameObject.GetComponent<컴포넌트이름>();

### 2. AddComponent 함수

- 게임 오브젝트에 컴포넌트를 추가하는 메소드이다.
- 다음과 같은 형식으로 사용한다.

    GameObject.AddComponent<컴포넌트이름>();

### 3. GameObject.Find

- 씬에 배치된 게임 오브젝트를 이름으로 검색한다.
- 검색한 게임 오브젝트를 결과로 반환한다.
- 다음과 같은 형식으로 사용한다.

    GameObject.Find("게임오브젝트이름");

### 4. GameObject.FindWithTag

- 씬에 배치된 게임 오브젝트를 태그로 검색한다.
- 검색한 게임 오브젝트를 결과로 반환한다.
- 다음과 같은 형식으로 사용한다.

    GameObject.FindWithTag("태그이름");
