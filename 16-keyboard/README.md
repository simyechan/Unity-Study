# Unity InputManager와 Input 클래스

## 1. Input Manager

Unity에서 **키보드, 마우스 등의 입력 설정을 관리**하는 기능이다.

* Unity에 설정된 입력 정보를 확인할 수 있다.
* 입력에 사용되는 키나 버튼 등의 설정을 확인하고 변경할 수 있다.
* `Input` 클래스를 통해 설정된 입력값을 확인하여 게임에서 사용할 수 있다.

---

## 2. Input 클래스

키보드, 마우스 등의 **사용자 입력에 관한 정보를 제공하는 클래스**이다.

### Input 주요 메서드

| 메서드                  | 설명                             |
| -------------------- | ------------------------------ |
| `Input.GetKey()`     | 지정한 키가 **눌려 있는 동안** `true`를 반환 |
| `Input.GetKeyDown()` | 지정한 키를 **누른 순간** `true`를 반환    |
| `Input.GetKeyUp()`   | 지정한 키를 **뗀 순간** `true`를 반환     |
| `Input.GetAxis()`    | 지정한 축의 입력값을 반환                 |

### 1) Input.GetKey()

특정 키가 **눌려 있는 동안** `true`를 반환한다.

```csharp
Input.GetKey(KeyCode.Space);
```

### 2) Input.GetKeyDown()

특정 키를 **누른 순간** `true`를 반환한다.

```csharp
Input.GetKeyDown(KeyCode.Space);
```

### 3) Input.GetKeyUp()

특정 키를 **뗀 순간** `true`를 반환한다.

```csharp
Input.GetKeyUp(KeyCode.Space);
```

### 4) Input.GetAxis()

Input Manager에 설정된 **축(Axis)의 입력값**을 반환한다.

```csharp
Input.GetAxis("Horizontal");
```

예를 들어 기본적으로 설정된 `"Horizontal"` 축은 일반적으로 `A/D` 또는 `←/→` 입력에 따라 `-1 ~ 1` 사이의 값을 반환한다.

```text
A 또는 ←  →  -1
입력 없음 →   0
D 또는 →  →   1
```
