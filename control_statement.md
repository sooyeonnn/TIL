# 제어문

크게 1. 조건문 2. 반복문으로 나뉜다.

## 제어문

파이썬은 기본적으로 위에서부터 아래로 차례대로 명령을 수행

특정 상황에 따라 코드를 선택적으로 실행하거나 계속하여 실행(반복)하는 제어가 필요함

제어문은 순서도(flowchart)로 표현 가능

**플로우차트를 많이 그려보는 것이 중요하다.**

--- 

# 조건문

조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용

ex) 조건이 참인가 -> True or False

- 조건식을 동시에 검사하는 것이 아니라 순차적으로 비교

- 처음 걸러진 조건의 값은 없어짐

- True 다음의 조건은 검증하지 않음. 그래서 else 는 남는 것. 조건이 모두 아닐 때 사용함

### 중첩 조건문

조건문 안의 조건문

들여쓰기에 유의하여 작성할 것

```python
if 조건:
    # code block
    if 조건
        # code block
else :
    # code block
```

### 조건 표현식

- 조건표현식이란
  
  - 조건표현식을 일반적으로 조건에 따라 값을 정할 때 활용
  
  - 삼항 연산자로 부르기도 함

- 문법: True인 경우 값 if 조건 else false인 경우 값
           ('왼참 오거'로 외우면 됨)

- 예시: value = num if num >= 0 else -num
  
            (절댓값을 저장하기 위한 코드)

--- 

# 반복문

### 반복문의 종류

- while문
  : 종료 조건에 해당하는 코드를 통해 반복문을 종료시켜야 함
  예시) 배가 부를 때까지 밥을 먹는다

- for문
  : 반복 가능한 객체를 모두 순회하면 종료(별도의 종료 조건이 필요 없음)
  예시) 10번만 한다.

- 반복 제어
  : break, continue, for-else

--- 

# while문

while문은 조건식이 참인 경우 반복적으로 코드를 실행

- 조건이 참인 경우 들여쓰기 되어 있는 코드 블록이 실행됨

- 코드 블록이 모두 실행되고, 다시 조건식을 검사하며 반복적으로 실행됨

- while문은 무한 루프를 하지 않도록 종료 조건이 반드시 필요 / 종료조건을 항상 생각하는 게 좋음

```python
a = 0

while a < 5:

    print(a)

    a += 1

print('끝')
```

### 복합연산자

복합연산자는 연산과 저장을 합쳐 놓은 것

예시) a += 1

--- 

# for문

for문은 시퀀스(string, tuple, list, range)를 포함한 순회 가능한 객체(literable)의 요소를 모두 순회

- 처음부터 끝까지 모두 순회하므로 별도의 종료 조건이 필요하지 않음 (한바퀴 돌면 알아서 끝남)

literable

- 순회할 수 있는 자료형(string, list, dict, tuple, range, set 등)

- 순회형 함수(range, enumerate)

문법)

for 변수명 in iterable:

    # code block

### 딕셔너리 순회

딕셔너리는 기본적으로 key를 순회하며, key값을 통해 값을 활용

```python
grades = {'john': 80, 'eric': 90}
for student in grades:
    print(student)
# john
# eric
```

```python
grades = {'john': 80, 'eric': 90}
for student in grades:
    print(student, grades[student])
# john 80
# eric 90
```

#### 추가 메서드를 활용한 딕셔너리 순회

- 추가 메서드를 활용하여 순회할 수 있음
  
  - keys(): key로 구성된 결과
  
  - value(): value로 구성된 결과
  
  - items(): (key, value)의 튜플로 구성된 결과

```python
grades = {'john': 80, 'eric': 90}
print(student.keys())   # dict_keys {['john', 'eric']}
print(student.values())  # dict_values {[80, 90]}
print(student.items())   # dict_items {[('john', 80), ('eric', 90)]}
```

```python
grades = {'john': 80, 'eric': 90}
for student, grade in grades.items():
    print(student, grade)


# john 80
# eric 90
```

### enumerate 순회

enumerate()

- 인덱스와 객체를 쌍으로 담은 열거형 객체 반환

- (index, value) 형태의 tuple로 구성된 열거 객체를 반환

- 인덱스가 필요한 경우에 많이 활용!

```python
members = ['민수', '영희', '철수']
enumerate(members) # enumerate at 0x105d3e100
print(list(enumerate(members))) # [(0,'민수'), (1, '영희'), (2, '철수')]
print(list(enumerate(members, start=1)))
# [(0,'민수'), (1, '영희'), (2, '철수')] => 숫자와 값의 튜
```

### List Comprehension

- 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성하는 방법

문법)

[code for 변수 in iterable]

[code for 변수 in iterable if 조건식]

```python
# 1~3의 세제곱 리스트 만들기
cubic_list = []
for number in range(1,4) :
    cubic_list.append(number ** 3)
print(cubic_list)
# [1, 8, 27]
```

### Dictionary Comprehension

```python
# 1~3의 세제곱 딕셔너리 만들기
cubic_dict = {}
for number in range(1,4) :
    cubic_dict[number] = (number ** 3)
print(cubic_dict)
# {1:1, 2:8, 3:27}
```

## 반복문 제어

- **break**
  : 반복문을 종료

```python
n = 0
while True :
    if n == 3 :
        break
    print(n)
    n += 1
# 0
# 1
# 2


------------------

for i in range(10):
    if i > 1:
        print('0과 1만 필요해!')
        break
    print(i)
# 0
# 1
# 0과 1만 필요해!
```

- **continue**
  : continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행 (스킵, 건너뛰기와 같다)

```python
for i in range(6) :
    if i % 2 == 0 :
        continue
    print(i)
# 1
# 3
# 5
```

- **for-else**
  :끝까지 반복문을 실행한 이후에 else문 실행
  break를 통해 중간에 종료되는 경우 else문은 실행되지 않음

```python
for char in 'apple':
    if char == 'b' :
    print('b!')
    break
else :
    print('b가 없습니다.')
# b가 없습니다.


---------
for char in 'banana':
    if char == 'b' :
    print('b!')
    break
else :
    print('b가 없습니다.')
# b!
```

- **pass**
  : 아무것도 하지 않음(문법적으로 필요하지만, 할 일이 없을 때 사용) (깍두기와 같다)

```python
# i가 2일 때 pass
for i in range(4) :
    if i == 2:
        pass
    print(i)
# 0
# 1
# 2
# 3
```
