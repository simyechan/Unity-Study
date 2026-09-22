# 배열과 반복문

## 1. 배열이란?

배열(Array)은 **연속된 메모리 공간에 여러 개의 데이터를 저장하는 자료구조**이다.

* 배열에 저장된 각각의 데이터를 **배열 원소(Element)** 라고 한다.
* 배열의 각 원소는 **인덱스(Index)** 를 통해 구분한다.
* 인덱스는 **0부터 시작**한다.

### 1) 1차원 배열

```csharp
데이터타입[] 변수이름 = new 데이터타입[원소개수];
```

예시:

```csharp
int[] numbers = new int[5];
```

### 2) 2차원 배열

```csharp
데이터타입[,] 변수이름 = new 데이터타입[2차원길이, 1차원길이];
```

예시:

```csharp
int[,] numbers = new int[2, 3];
```

---

## 2. 여러 개의 GameObject 검색

특정 태그를 가진 **모든 GameObject를 검색**할 때 사용한다.

```csharp
GameObject.FindGameObjectsWithTag("태그이름");
```

예시:

```csharp
GameObject[] enemies = GameObject.FindGameObjectsWithTag("Enemy");
```

* 지정한 태그를 가진 모든 GameObject를 배열로 반환한다.
* 여러 개의 GameObject를 한 번에 검색할 때 사용할 수 있다.

---

## 3. 반복문의 종류

반복문은 **특정 조건이 만족되는 동안 코드를 반복해서 실행**할 때 사용한다.

### 1) for문

반복 횟수가 정해져 있거나 반복 횟수를 직접 제어할 때 주로 사용한다.

```csharp
for (변수 = 초기값; 조건식; 변수증감)
{
    코드블럭
}
```

예시:

```csharp
for (int i = 0; i < 5; i++)
{
    Debug.Log(i);
}
```

---

### 2) while문

조건식이 `true`인 동안 코드를 반복해서 실행한다.

```csharp
while (조건식)
{
    코드블럭
}
```

예시:

```csharp
int i = 0;

while (i < 5)
{
    Debug.Log(i);
    i++;
}
```

---

### 3) do-while문

`do` 블록의 코드를 **최소 한 번 실행한 후** 조건식을 검사한다.

```csharp
do
{
    코드블럭
}
while (조건식);
```

예시:

```csharp
int i = 0;

do
{
    Debug.Log(i);
    i++;
}
while (i < 5);
```

---

### 4) foreach문

배열이나 컬렉션의 **모든 요소를 하나씩 순회**할 때 사용한다.

```csharp
foreach (데이터타입 변수명 in 배열)
{
    코드블럭
}
```

예시:

```csharp
int[] numbers = { 1, 2, 3, 4, 5 };

foreach (int number in numbers)
{
    Debug.Log(number);
}
```

> `foreach`문은 배열의 처음부터 끝까지 각 원소를 하나씩 가져와서 코드를 실행한다.
