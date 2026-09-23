# Unity Collider와 Rigidbody, 충돌 처리

## 1. Collider

`Collider`는 **물체의 충돌 영역을 정의하고 충돌을 감지하기 위해 사용하는 컴포넌트**이다.

* GameObject의 물리적인 충돌 영역을 설정한다.
* 다른 Collider와의 충돌을 감지할 수 있다.
* `Box Collider`, `Sphere Collider`, `Capsule Collider` 등 다양한 종류가 있다.
* Collider 자체가 물리적인 움직임을 계산하는 것은 아니며, `Rigidbody`와 함께 사용하면 물리 엔진을 이용한 충돌 처리가 가능하다.

---

## 2. Rigidbody

`Rigidbody`는 GameObject에 **물리적인 움직임을 적용하기 위해 사용하는 컴포넌트**이다.

* 중력의 영향을 받을 수 있다.
* 힘이나 충격을 받아 이동할 수 있다.
* 물리적인 회전을 구현할 수 있다.
* `Rigidbody`와 `Collider`를 함께 사용하여 물리 기반의 충돌을 구현할 수 있다.

---

## 3. 충돌 처리

Unity에서 GameObject의 충돌은 크게 **Collision**과 **Trigger**로 구분할 수 있다.

| 구분            | 설명                     |
| ------------- | ---------------------- |
| **Collision** | 물리적인 충돌이 발생하며 물리량이 적용됨 |
| **Trigger**   | 물리적인 충돌 없이 영역의 겹침을 감지함 |

### 충돌 처리를 위한 주요 요소

일반적인 물리 충돌을 구현하기 위해서는 다음과 같은 컴포넌트를 사용한다.

```text
Rigidbody
   +
Collider
   ↓
물리적인 충돌 처리
```

---

## 4. Collision 관련 함수

`Collision`은 두 Collider가 실제로 충돌하여 **물리적인 충돌이 발생했을 때** 호출되는 함수이다.

### 1) OnCollisionEnter()

충돌이 **처음 발생했을 때** 한 번 호출된다.

```csharp id="8y6t2k"
private void OnCollisionEnter(Collision collision)
{
    // 충돌이 처음 발생했을 때 실행
}
```

### 2) OnCollisionStay()

충돌이 **지속되는 동안** 매 프레임 호출된다.

```csharp id="7z0j3m"
private void OnCollisionStay(Collision collision)
{
    // 충돌이 지속되는 동안 실행
}
```

### 3) OnCollisionExit()

충돌이 **끝나는 순간** 한 번 호출된다.

```csharp id="w7u4a2"
private void OnCollisionExit(Collision collision)
{
    // 충돌이 끝났을 때 실행
}
```

---

## 5. Trigger 관련 함수

`Trigger`는 물리적인 충돌을 발생시키지 않고 **두 Collider가 영역을 겹치는지 감지**할 때 사용한다.

Collider의 **Is Trigger** 옵션을 활성화하면 Trigger로 사용할 수 있다.

### 1) OnTriggerEnter()

Trigger 영역에 **처음 들어왔을 때** 호출된다.

```csharp id="9e4x8s"
private void OnTriggerEnter(Collider other)
{
    // Trigger 영역에 들어왔을 때 실행
}
```

### 2) OnTriggerStay()

Trigger 영역에 **머무르는 동안** 매 프레임 호출된다.

```csharp id="5c2w1f"
private void OnTriggerStay(Collider other)
{
    // Trigger 영역에 머무르는 동안 실행
}
```

### 3) OnTriggerExit()

Trigger 영역에서 **나갔을 때** 호출된다.

```csharp id="2n8k5v"
private void OnTriggerExit(Collider other)
{
    // Trigger 영역에서 나갔을 때 실행
}
```

---

## 6. Collision과 Trigger 비교

| 구분       | Collision            | Trigger               |
| -------- | -------------------- | --------------------- |
| 물리적인 충돌  | O                    | X                     |
| 물리량 적용   | O                    | X                     |
| 영역 겹침 감지 | O                    | O                     |
| Enter    | `OnCollisionEnter()` | `OnTriggerEnter()`    |
| Stay     | `OnCollisionStay()`  | `OnTriggerStay()`     |
| Exit     | `OnCollisionExit()`  | `OnTriggerExit()`     |
| 주요 용도    | 벽, 바닥, 물체 충돌 등       | 아이템 획득, 특정 영역 진입 감지 등 |
