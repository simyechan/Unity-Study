# Unity 마우스 입력과 Picking

## 1. 마우스 위치

화면상의 마우스 위치는 `Input.mousePosition`을 사용하여 확인할 수 있다.

```csharp
Input.mousePosition
```

* 화면 좌표는 **화면의 좌측 하단을 원점 `(0, 0)`** 으로 한다.
* `x`축은 오른쪽으로 갈수록 증가한다.
* `y`축은 위쪽으로 갈수록 증가한다.

```text
(0, Screen.height) ─────────── (Screen.width, Screen.height)
        │
        │
        │
        │
      (0, 0) ───────────────── (Screen.width, 0)
```

---

## 2. 마우스 버튼 번호

Unity에서는 마우스 버튼을 번호로 구분한다.

| 버튼         |  번호 |
| ---------- | --: |
| 마우스 왼쪽 버튼  | `0` |
| 마우스 오른쪽 버튼 | `1` |
| 마우스 휠 버튼   | `2` |

예시:

```csharp
Input.GetMouseButtonDown(0);
```

위 코드는 **마우스 왼쪽 버튼을 누른 순간**을 확인한다.

---

## 3. 마우스 관련 메서드

### 1) Input.GetMouseButton()

지정한 마우스 버튼을 **누르고 있는 동안** `true`를 반환한다.

```csharp
Input.GetMouseButton(마우스버튼번호);
```

예시:

```csharp
Input.GetMouseButton(0);
```

---

### 2) Input.GetMouseButtonDown()

지정한 마우스 버튼을 **누른 순간** `true`를 반환한다.

```csharp
Input.GetMouseButtonDown(마우스버튼번호);
```

예시:

```csharp
Input.GetMouseButtonDown(0);
```

---

### 3) Input.GetMouseButtonUp()

지정한 마우스 버튼을 **뗀 순간** `true`를 반환한다.

```csharp
Input.GetMouseButtonUp(마우스버튼번호);
```

예시:

```csharp
Input.GetMouseButtonUp(0);
```

---

### 4) Input.GetAxis()

마우스의 이동 및 휠 입력값을 가져올 때 사용할 수 있다.

```csharp
Input.GetAxis(axisName);
```

---

## 4. 마우스 축 이름 (axisName)

| 축 이름                  | 설명         |
| --------------------- | ---------- |
| `"Mouse X"`           | 마우스의 X축 이동 |
| `"Mouse Y"`           | 마우스의 Y축 이동 |
| `"Mouse ScrollWheel"` | 마우스 휠의 스크롤 |

예시:

```csharp
float mouseX = Input.GetAxis("Mouse X");
float mouseY = Input.GetAxis("Mouse Y");
float scroll = Input.GetAxis("Mouse ScrollWheel");
```

---

## 5. 마우스 Picking

**마우스로 선택한 GameObject 또는 좌표를 얻어내는 방법**이다.

마우스로 화면을 클릭하면 해당 화면 좌표를 기준으로 **게임 월드 안쪽으로 광선(Ray)을 발사**하고, 광선과 GameObject의 교차 여부를 확인하여 클릭한 대상을 찾을 수 있다.

### Picking 과정

```text
마우스 클릭
    ↓
화면 좌표 확인
    ↓
화면 좌표를 기준으로 Ray 생성
    ↓
게임 월드로 Ray 발사
    ↓
GameObject와의 교차 여부 확인
    ↓
충돌한 GameObject 확인
```

### 1) Ray 생성

```csharp
Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
```

`ScreenPointToRay()`는 **화면상의 마우스 위치를 기준으로 게임 월드 방향으로 향하는 Ray를 생성**한다.

* `Input.mousePosition` → 화면상의 마우스 위치
* `Camera.main` → Main Camera
* `ScreenPointToRay()` → 화면 좌표를 기반으로 Ray 생성

---

### 2) Raycast를 이용하여 GameObject 검색

```csharp
Physics.Raycast(Ray, out RaycastHit, 최대거리);
```

Ray를 발사하여 **게임 공간의 Collider와 교차하는지 확인**하고, 충돌 정보를 얻을 수 있다.

예시:

```csharp
Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

if (Physics.Raycast(ray, out RaycastHit hit, 100f))
{
    Debug.Log(hit.collider.gameObject.name);
}
```

위 코드는 마우스 위치에서 Ray를 발사하고, **최대 100의 거리 내에서 충돌한 GameObject의 이름을 출력**한다.

> `Physics.Raycast()`는 GameObject 자체가 아니라 **Collider와의 충돌 여부**를 검사한다. 따라서 Picking하려는 GameObject에는 Collider가 필요하다.
