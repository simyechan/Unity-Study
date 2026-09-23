# Unity 애니메이션 시스템

## 1. 애니메이션 구분

Unity의 애니메이션 시스템은 크게 **Legacy** 방식과 **Mechanim** 방식으로 구분할 수 있다.

### 1) Legacy

`Mechanim`이 사용되기 전에 사용하던 **기존의 간단한 애니메이션 시스템**이다.

* `Animation` 컴포넌트를 사용한다.
* 코드에서 애니메이션을 직접 재생하거나 제어할 수 있다.
* 현재는 주로 기존 프로젝트나 간단한 애니메이션에서 사용된다.

### 2) Mechanim

Unity의 **상태 머신(State Machine)을 기반으로 애니메이션을 관리하는 시스템**이다.

* `Animator` 컴포넌트를 사용한다.
* `Animator Controller`를 이용하여 애니메이션 상태를 구성한다.
* 상태 간의 전환을 설정할 수 있다.
* `Parameter`를 사용하여 애니메이션 상태 전이를 제어할 수 있다.

---

## 2. 애니메이션 파일

Unity에서 애니메이션이 포함된 파일은 파일 이름에 **`@` 문자가 포함된 형태**로 표시되는 경우가 있다.

예시:

```text
Character@Idle.fbx
Character@Walk.fbx
Character@Run.fbx
```

---

## 3. Wrap Mode

`Wrap Mode`는 **Legacy 방식에서 애니메이션 클립의 재생 범위를 벗어난 시간에 애니메이션을 어떻게 처리할지 결정하는 설정**이다.

대표적인 설정:

| Wrap Mode      | 설명                   |
| -------------- | -------------------- |
| `Once`         | 애니메이션을 한 번 재생        |
| `Loop`         | 애니메이션을 반복 재생         |
| `PingPong`     | 애니메이션을 정방향과 역방향으로 반복 |
| `ClampForever` | 마지막 프레임을 계속 유지       |

예시:

```csharp id="9p5h1a"
animation.wrapMode = WrapMode.Loop;
```

위 코드는 애니메이션을 반복 재생하도록 설정한다.

---

## 4. Legacy 애니메이션 관련 메서드

Legacy 방식에서는 `Animation` 컴포넌트를 통해 애니메이션을 제어할 수 있다.

### 1) Animation.Play()

현재 설정된 애니메이션을 재생한다.

```csharp id="8s7k3d"
animation.Play();
```

### 2) Animation.Stop()

재생 중인 애니메이션을 정지한다.

```csharp id="5f2m9x"
animation.Stop();
```

### 3) Animation.Play(string)

지정한 이름의 애니메이션을 재생한다.

```csharp id="4q6v8n"
animation.Play("Animation Name");
```

### 4) Animation.Stop(string)

지정한 이름의 애니메이션을 정지한다.

```csharp id="1j7c4p"
animation.Stop("Animation Name");
```

### 5) Animation.IsPlaying(string)

지정한 이름의 애니메이션이 현재 재생 중인지 확인한다.

```csharp id="6b3w9k"
animation.IsPlaying("Animation Name");
```

반환값은 `bool`이다.

```csharp id="0m8x2q"
if (animation.IsPlaying("Walk"))
{
    Debug.Log("Walk 애니메이션 재생 중");
}
```

### 6) Animation.CrossFade()

현재 재생 중인 애니메이션에서 다른 애니메이션으로 **부드럽게 전환**한다.

```csharp id="7n4d5s"
animation.CrossFade("Animation Name", 0.2f);
```

두 번째 매개변수는 애니메이션 전환에 걸리는 시간이다.

### 7) Animation.wrapMode

애니메이션의 반복 방식을 설정한다.

```csharp id="3k9p1v"
animation.wrapMode = WrapMode.Loop;
```

### 8) Animation[].speed

특정 애니메이션의 재생 속도를 설정한다.

```csharp id="2h6m8r"
animation["Animation Name"].speed = 2.0f;
```

`1.0f`가 기본 속도이며, `2.0f`로 설정하면 2배 빠르게 재생된다.

---

## 5. Mechanim 애니메이션

Mechanim 방식에서는 **`Animator` 컴포넌트**를 사용하여 애니메이션을 관리한다.

### 1) Animator 컴포넌트

GameObject에 `Animator` 컴포넌트를 추가하여 애니메이션을 재생하고 관리한다.

```text
GameObject
└── Animator
```

### 2) Animation Controller

`Animator Controller`에서 **상태 머신(State Machine)** 을 구성하여 애니메이션의 상태와 전이를 관리한다.

예시:

```text
[Idle]
   │
   │ 이동
   ↓
[Walk]
   │
   │ 이동 중지
   ↓
[Idle]
```

### 3) Parameter

`Animator Controller`에 **Parameter**를 등록하여 애니메이션 상태 전이에 사용할 수 있다.

대표적인 Parameter 종류:

| Parameter | 설명           |
| --------- | ------------ |
| `Float`   | 실수형 값        |
| `Int`     | 정수형 값        |
| `Bool`    | 참/거짓 값       |
| `Trigger` | 한 번 발생하는 이벤트 |

예를 들어 `Bool` 타입의 `isWalk` Parameter를 사용하여 걷기 상태로 전환할 수 있다.

```text
isWalk == false
       ↓
    [Idle]
       │
       │ isWalk == true
       ↓
    [Walk]
```

### Legacy와 Mechanim 비교

| 구분        | Legacy            | Mechanim    |
| --------- | ----------------- | ----------- |
| 주요 컴포넌트   | `Animation`       | `Animator`  |
| 애니메이션 관리  | 코드 중심             | 상태 머신 중심    |
| 상태 머신     | X                 | O           |
| Parameter | X                 | O           |
| 주요 용도     | 기존 시스템, 간단한 애니메이션 | 캐릭터 애니메이션 등 |
