# Unity 리소스와 List

## 1. Unity Asset Store

Unity에서 제공하는 **Asset 상점**으로, 게임 개발에 필요한 다양한 Asset을 구매하거나 판매할 수 있는 곳이다.

* 3D 모델
* 2D 이미지
* 애니메이션
* 사운드
* 에셋 및 플러그인 등

---

## 2. 리소스 로드 방법

`Resources` 폴더에 리소스를 저장한 후 `Resources.Load()` 메서드를 이용하여 리소스를 로드할 수 있다.

### 1) Resources 폴더 생성

프로젝트의 `Assets` 폴더 아래에 `Resources` 폴더를 생성하고 사용할 리소스를 저장한다.

```text
Assets
└── Resources
    └── 프리팹이름.prefab
```

### 2) Resources.Load()를 이용하여 리소스 로드

```csharp
Resources.Load("프리팹이름");
```

예시:

```csharp
GameObject prefab = Resources.Load<GameObject>("Enemy");
```

> `Resources.Load()`의 경로에는 `Resources` 폴더 자체는 포함하지 않는다.

---

## 3. 인스턴스 생성

리소스로 로드한 `GameObject`를 실제 씬에 생성하는 것을 **인스턴스 생성**이라고 한다.

```csharp
Instantiate(로드한게임오브젝트);
```

예시:

```csharp
GameObject prefab = Resources.Load<GameObject>("Enemy");

Instantiate(prefab);
```

* `Resources.Load()` → 리소스를 메모리에 로드
* `Instantiate()` → 로드한 GameObject의 인스턴스를 생성

---

## 4. GameObject 삭제

### 1) Destroy(GameObject)

씬에 존재하는 GameObject를 삭제한다.

```csharp
Destroy(게임오브젝트);
```

예시:

```csharp
Destroy(enemy);
```

### 2) Destroy(GameObject, 시간)

지정한 시간이 지난 후 GameObject를 삭제한다.

```csharp
Destroy(게임오브젝트, 시간);
```

예시:

```csharp
Destroy(enemy, 3.0f);
```

위 코드는 `enemy`를 **3초 후에 삭제**한다.

---

## 5. List

`List`는 데이터를 **추가하거나 삭제할 수 있는 동적 자료구조**이다.

* 여러 개의 데이터를 순서대로 저장할 수 있다.
* 필요한 경우 데이터의 추가 및 삭제가 가능하다.
* 동적으로 메모리를 할당하여 사용한다.
* 배열은 생성 시 크기가 결정되지만, `List`는 필요에 따라 크기가 변경될 수 있다.

### 1) List 선언

```csharp
List<데이터타입> 리스트변수명 = new List<데이터타입>();
```

예시:

```csharp
List<int> numbers = new List<int>();
```

### 2) 데이터 추가

`Add()` 메서드를 사용하여 데이터를 추가한다.

```csharp
리스트변수명.Add(추가할데이터);
```

예시:

```csharp
numbers.Add(10);
numbers.Add(20);
numbers.Add(30);
```

### 3) 데이터 삭제

`Remove()` 메서드를 사용하여 특정 원소를 삭제한다.

```csharp
리스트변수명.Remove(원소);
```

예시:

```csharp
numbers.Remove(20);
```

### 4) List의 모든 데이터 삭제

`Clear()` 메서드를 사용하여 List의 모든 원소를 삭제한다.

```csharp
리스트변수명.Clear();
```

예시:

```csharp
numbers.Clear();
```

### List 주요 메서드 정리

| 메서드        | 설명        |
| ---------- | --------- |
| `Add()`    | 데이터 추가    |
| `Remove()` | 특정 데이터 삭제 |
| `Clear()`  | 모든 데이터 삭제 |
