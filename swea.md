# 문자열 리스트를 정수로 변환

### 새로운 리스트 = list(map(int, 리스트이름))

string_list = ['100', '140', '8' ,'209', '50' '92', '3']
print(string_list)

int_list = list(map(int, string_list))
print(int_list)

---

# 문자열을 분할한 리스트 생성

### split() 사용

t = input()
t_list = t.split()



--- 

# 파이썬 예외 처리

**try**:
    실행할 코드
**except**:
    에러 발생 시 수행할 코드
**else**:
    에러가 없을 시 수행할 코드
**finally**: 
    에러와 상관없이 수행할 코드

* 참고: 파이썬 예외처리로 검색하면 많이 나온다.

```python
a = [1,2,3]
for i in range(4):
    try :
        print(a[i])
    except:
        print('잘못된 인덱스 접근입니다.')
    finally :
        print('에러와 상관없이 수행')
```

--- 
# sys.stdin.readline() 사용법
### 한 개의 정수 입력

```python
import sys
a = int(sys.stdin.readline())
```

### 정해진 개수의 정수를 한줄에 입력받을 때
```python
import sys
a,b,c = map(int,sys.stdin.readline().split())
```
###  임의의 개수의 정수를 한줄에 입력받아 리스트에 저장할 때
```python
import sys
data = list(map(int,sys.stdin.readline().split()))
```

### 임의의 개수의 정수를 n줄 입력받아 2차원 리스트에 저장할 때
```python
import sys
data = []
n = int(sys.stdin.readline())
for i in range(n):
    data.append(list(map(int,sys.stdin.readline().split())))
```

### 문자열 n줄을 입력받아 리스트에 저장할 때
```python
import sys
n = int(sys.stdin.readline())
data = [sys.stdin.readline().strip() for i in range(n)]
```
