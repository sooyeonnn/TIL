# 데이터 구조 활용

컨테이너라고 배웠던 것들
컨테이너를 더 쉽고 편하게 사용할 수 있도록 해주는 메소드

메서드는 클래스 내부에 정의된 함수 == 사실상 함수와 동일하다.
나중에 배울 객체와 관련돼서 학습하게 될 것이다.

데이터 구조(리스트, 세트, 튜플).메서드() 형태로 활용한다.
어렵게 느껴진다면! 주어.동사()
ex)교수.말하기()
ex)list.append(10) # 리스트의 원소를 추가하는 메소드 append()
ex)string.split() # 문자열의 단어를 알파벳으로 쪼개는 매소드 split()


--- 

###### 파이썬 공식문서에서 사용하는 메소드의 표기법(베커스-나우르 표기법)
프로그래밍 언어의 구문을 기술하는데 사용하는 자연스러운 표기법
str(사용가능한 데이터(객체)).메소드의이름(파라미터1, 파라미터2[,파라미터3])
파라미터1과 파라미터2는 필수
파라미터3은 선택

str.replace(old, new [,count])
old = 원래 있던 문자열(바꿀 대상)
new = 원래 있던 문자열을 어떤 문자열로 바꾸고 싶은지

--- 

# 문자열(string type)
: 문자들의 나열
- 문자열을 사용할 때는 ''나 ""를 사용해서 묶어줘야 한다.
- 모든 문자는 str타입 (변경 불가능한 immutable)

``` python
word = 'johnny' 
print(id(word)) # 메모리 주소 확인 2927003137456
word = 'test'
print(id(word)) # 메모리 주소 확인 2927003165232

# 변경된 것이 아니라, 새로운 것이 생긴 것임 : immutable 
# 바뀐게 아니라 갈아끼우기 한 것
```


###### 문자열 조회/탐색 및 검증 메서드
- **s.find(x)** : x의 첫번째 위치를 반환. 없으면, -1을 반환(string type에서만 사용가능)
- **s.index(x)**: x의 첫번째 위치를 반환. 없으면, 오류 발생(리스트 튜플 등 다른 컨테이너도 사용가능하다)
- s.isalpha(): 알파벳 문자여부를 묻는 메서드 * 단순 알파벳이 아닌 유니코드 상 letter(한국어도 포함) - 알파벳이랑 유사한 것도 포함
- s.isupper(): 문자열이 대문자로 이루어져 있는지 여부
- s.islower(): 문자열이 소문자로 이루어져 있는지 여부
- s.istitle() : 타이틀 형식 여부


``` python
# find와 index의 차이점
print('apple'.find('p')) # 1
print('apple'.find('k')) # -1 / 문자열에 찾는 문자가 존재하지 않으면 -1반환

string1 = 'apple'
print(string1.index('p')) # 1 / 제일 처음 찾는 p의 위치를 출력
print(string1.index('i')) # 에러

my_list = list(string1)
print(my_list.index('p')) # 1
print(my_list.find('p')) # 사용불가

print('---------------------')

print('johnny'.isalpha()) # True : 숫자냐 숫자가 아니냐를 나눔
print('쟈니'.isalpha()) # True : 숫자냐 숫자가 아니냐를 나눔
print('Entp'.isupper()) # False

```

###### 문자열 관련 검증 메서드
.isdecimal() .isdigit() .isnumeric()
주로 .isdecimal() 사용하여 해결


###### 문자열 변경 메서드
- **s.replace(old, new[,count]** :바꿀 대상 글자를 새로운 글자로 바꿔서 반환
- **s.strip([chars])** : 공백이나 특정 문자를 제거
- s.split(sep=None, maxsplit=-1): 공백이나 특정 문자를 기준으로 분리
- 'separator'.hoin([iterable]) : 구분자로 iterable을 합침
- s.capitalize(): 가장 첫번째 글자를 대문자로 변경
- **s.join()** : 구분자를 통해 주어진 리스트나 순회가능한 객체를 합쳐주는 메서드 / "".join(리스트) : 리스트를 문자열로 바꾸는 코드

``` python
print('coone'.replace('o', 'a')) # caane
print('coooone'.replace('o', 'a', 2)) # caaoone / 두 개만 바꾼다

print('            와우\n'.strip()) # 와우

print('N,C,T'.split(',')) # ['N', 'C', 'T'] / 문자열에서 , 단위로 분리된 리스트를 반환한다.
print('N C T'.split()) # ['N', 'C', 'T'] / 인자를 제공하지 않으면 공백 단위로 쪼갠 리스트를 반환한다.

print('!'.join('ssafy')) # s!s!a!f!y
my_list = ['a', 'b', 'c', 'd', 'e']
print("".join(my_list)) # abcde
print(",".join(my_list)) # a,b,c,d,e

msg = 'hI! everyone, I\'m ssafy'
print(msg)                  # hI! everyone, I'm ssafy
print(msg.capitalize())     # Hi! everyone, i'm ssafy
print(msg.title())          # Hi! Everyone, I'M Ssafy
print(msg.upper())          # HI! EVERYONE, I'M SSAFY
print(msg.lower())          # hi! everyone, i'm ssafy
print(msg.swapcase())       # Hi! EVERYONE, i'M SSAFY

print('*'.join('ssafy'))
print(' '.join(['1', '2', '7']))
print(''.join(['1', '2', '7']))
```

--- 

# 리스트
리스트는 여러개의 값을 순서가 있는 구조로 저장할 때 사용
대괄호([]) 또는 list()를 사용해서 생성

- 2차원 리스트: 리스트 안에 리스트가 존재
- 이런 유연성 때문에 파이썬에서 가장 흔하게 사용되는 데이터 구조다.
- 순서가 있는 데이터 구조이기 때문에 인덱스를 통해 접근이 가능하다.


###### 리스트 메서드
- **L.append(x)** : 리스트 **마지막**에 항목 x를 추가
- **L.insert(i, x)**: 리스트 **특정 위치**(인덱스 i)에 항목 x를 삽입
- L.remove(x) : 리스트 가장 왼쪽에 있는 항목(첫번째) x를 제거 / 항목이 존재하지 않는 경우 에러
- L.pop(): 리스트 가장 오른쪽에 있는 항목(마지막)을 반환 후 제거
- L.pop(i): 리스트의 인덱스 i에 있는 항목을 반환 후 제거
- L.extend(m): 순회형 m의 모든 항목들의 리스트 끝에 추가 (+=과 같은 기능)
- L.index(x, startm end): 리스트에 있는 항목중 가장 왼쪽에 있는 항목 x의 인덱스를 반환
- L.reverse(): 리스트를 거꾸로 정렬
- L.sort() : 리스트를 정렬


###### 값 추가 및 삭제
- .insert(i, x)
```python
cafe = ['starbucks', 'hollys']

# insert() 첫번째 인자는 인덱스 넘버, 두번째 인자는 넣고 싶은 값
cafe.insert(1, '7dream') 
print(cafe) # ['starbucks', '7dream', 'hollys']
# 인자로 위치를 전달할 때 그 위치가 리스트의 범위를 벗어난 경우에는 맨마지막에 추가된다.
cafe.insert(50, 'wayv')
print(cafe) # ['starbucks', '7dream', 'hollys', 'wayv']


# append() 맨 마지막에 추가한다
cafe.append('127')
print(cafe) # ['starbucks', '7dream', 'hollys', '127']


cafe.extend(['coffee']) 
print(cafe) # ['starbucks', '7dream', 'hollys', 'coffee']

cafe.extend('coffee')
print(cafe) # ['starbucks', '7dream', 'hollys', 'coffee', 'c', 'o', 'f', 'f', 'e', 'e']

# remove 메서드는 인덱스를 인자로 주는 게 아니라 삭제하고 싶은 데이터를 인자로 전달한다.
# remove는 삭제할 대상이 포함되어 있지 않으면 에러 발생
cafe.remove('hollys')
print(cafe) # ['starbucks', '7dream', 'coffee', 'c', 'o', 'f', 'f', 'e', 'e']


print('----------------------------------------')


numbers = [1, 2, 3, 'hi']
print(numbers) # [1, 2, 3, 'hi']

word = numbers.pop()
print(numbers) # [1, 2, 3]
print(word) # hi

numbers.clear()
print(numbers) # []


print('----------------------------------------')

numbers = [1, 2, 3, 1, 1, 1, 32, 43,2]
print(numbers.count(1))      # 4
print(numbers.count(100))    # 0 : 없어도 오류가 나지 않음

```

- sort()와 sorted()의 차이
-- .sort() - 원본을 바꿈
-- .sorted - 

``` python
numbers = [3, 2, 5, 7]
result = numbers.sort() 
# sort() 메서드는 리턴값이 None ==> 데이터 자체를 정렬한다.(자기자신)
print(numbers, result) # [2, 3, 5, 7] None


# 정렬 결과를 다른곳에 저장하고 싶을 때는 ==> sorted()
numbers = [3, 2, 6, 8]
# result = numbers.sorted() (X): 자주 하는 실수
result = sorted(numbers)
print(numbers, result) # [3, 2, 6, 8] [2, 3, 6, 8] 
# 결과만 보면 result에 정렬한 결과가 저장
# numbers는 정렬이 되지 않은 상태 그대로
# 원본 데이터를 보존하고 싶을 때는 sorted()를 사용해야 한다.


numbers = [3, 2, 5, 1]
result = numbers.reverse()
print(result, numbers)  # None [1, 5, 2, 3]
# reverse() 메소드의 반환값은 None
# reverse() 메소드를 실행한다고 해서 내부적으로 정렬이 되지는 않는다.
# 순서만 반대로 뒤집을 뿐이다.

```

--- 

# 튜플
튜플은 여러 개의 값을 순서가 있는 구조로 저장하고 싶을 때 사용한다.
(리스트와 비슷)
- 리스트와의 차이점: 생성 후에 담고 있는 값은 변경이 불가능하다(중요)

생성시 ()를 사용해서 생성

```python
# 리스트에는 extend()라는 메서드가 있느느데, 튜플에서는 사용이 불가능
my_list = [1, 2, 3, 4]
my_tuple = (1, 2, 3, 4) # 튜플은 읽기 전용

#my_list.extend([5, 6]) # 가능
#my_tuple.extend((5, 6)) # 불가

my_list += 5, 6
print(my_list) # [1, 2, 3, 4, 5, 6]
my_tuple += 5, 6
print(my_tuple) # (1, 2, 3, 4, 5, 6)

# 튜플은 분명히 변경 불가능한데 + 연산자는 사용이 가능하네요?
# += 연산자를 이용해서 튜플에 원소를 추가하면
# my_tuple 이라는 변수 안에 !새로운 튜플!을 만들어서 저장
# extend 는 자기 자신에 변경을 하는 것이므로 안되는 것!

```


```python
day_name = ('월', '화', '수', '목', '금')

print(type(day_name))
print(id(day_name))   # 2286034111920
print(day_name[-3]) # 수
print(day_name * 2) # ('월', '화', '수', '목', '금', '월', '화', '수', '목', '금')
day_name += False, True
print(day_name) # ('월', '화', '수', '목', '금', False, True)
print(id(day_name)) # 2286035498944 같은 튜플이 아닌, 새로 만들어진 튜플임
```

- 멤버십 연산자
: 멤버십 연산자 in을 통해 있는지 확인
``` python
print('aaple' in 'a') # False (X) - 거꾸로 써야 함
print('a' in 'aaple') # True

print('hi' in 'hi I am SSAFY') # True
```


- 시퀀스형 연산자
-- 산술연산자 (+) : 시퀀스 간의 concatenation
-- 반복연산자 (*) : 시퀀스를 반복


--- 

# 셋
중복 요소가 존재하지 않는 자료구조
중복되는 원소가 존재하면 하나만 남겨놓고 나머지는 다 제거
순서가 없기 때문에 인덱스로 접근이 불가능하다

수학에서의 집합을 표현한 자료구조
집합 연산이 가능하다.

담고 있는 요소를 삽입, 변경, 삭제가 가능하다.

###### 셋 메서드
- s.copy(): 셋의 얕은 복사본을 반환
- s.add(x): 항목 x가 셋 s에 없다면 추가
- s.pop(): 셋 s에서 랜덤하게 항목을 반환(순서가 없기 때문)하고, 해당 항목을 제거 / set이 비어있을 경우, keyError
- s.remove(x): 항목 x를 s에서 삭제, 항목이 존재하지 않을 경우, keyerror 발생
- s.discard(x): 항목x가 셋 s에 있는 경우, 항목 x를 셋에서 삭제, 없어도 오류 안남

s.ifdifjoint(t): 서로소인지 확인


###### 추가 변경
.add(elem) : 셋에 값을 추가
.update(*others) : 여러 값을 추가, 세트 두개를 대상으로 세트를 업데이트 하는 메서드(합집합)

```python
a = {'사과', '바나나', '수박'}
a.update(['딸기', '바나나', '참외']) 
print(a) # {'바나나', '참외', '수박', '사과', '딸기'}
b = ["딸기", "두리안", "포도"]
a.update(b) # {'바나나', '두리안', '포도', '참외', '수박', '사과', '딸기'}

```
###### 요소 삭제
.remove(elem) : 요소를 삭제, 요소가 없으면 에러 - 무조건 삭제할 것이 있어야 할 때 사용
.discard(elem) : 요소를 삭제, 없어도 에러가 나지 않음
```python
a.remove('딸기')
print(a) # {'수박', '바나나', '사과', '참외'}

a.discard('딸기')
print(a) # {'수박', '바나나', '사과', '참외'}
a.discard('딸기')
print(a) # {'수박', '바나나', '사과', '참외'}

```
.pop() : 임의의 원소를 제거해 반환
.clear() : 모든 항목을 제거

###### 집합관련 함수
s.isdisjoin(t): 서로소인가? 교집합이 없는가?
s.issubset(t): s가 t의 하위셋인가?
s.issuperset(t): s가 t의 상위셋인가?
```python
a = {'사과', '바나나', '수박'}
b = {'포도', '망고'}
c = {'사과', '포도', '망고', '수박', '바나나'}

print(a.isdisjoint(b)) # a와 b가 서로소인가? True
print(a.isdisjoint(c)) # a와 c가 서로소인가? False
print(a.issubset(c)) # a가 c의 하위셋인가? True
print(b.issubset(c)) # b가 c의 하위셋인가? True
print(c.issuperset(a)) # c가 a의 상위셋인가? True
print(c.issuperset(b)) # c가 b의 상위셋인가? True
print(b.issubset(a)) # b가 a의 하위셋인가? False
```

--- 


# 딕셔너리
키-값 쌍으로 이뤄진 자료구조(파이썬 3.7 버전부터 순서를 기억할 수 있게 되었다.)
- key는 변경 불가능한 데이터만 활용가능
- 값은 어떤 형태든 상관 없다.(리스트, 딕셔너리도 가능)

```python

my_dict = {'apple' : '사과', 'banana' : '바나나'}
# 키를 통해서 저장된 값을 가져올 수 있다.

# apple에 저장된 값을 알고 싶다?
print(my_dict['apple']) # 사과
print(my_dict.get('apple')) # 사과
print(my_dict.get('grape')) # None
print(my_dict.get('grape', '해당과일없음')) # 해당과일없음 / get()의 두번째 인자로 기본값을 제공해 줄 수 있다. 기본값은 딕셔너리에 해당 키가 없을 때 동작하게 된다.

# 딕셔너리 안의 값을 수정하고 싶다.
# 수정할 값에 매칭되는 키를 통해 update() 메소드를 사용한다.

my_dict.update(apple = '썩은사과')
print(my_dict) # {'apple': '썩은사과', 'banana': '바나나'}
# ==
my_dict['apple'] = '썩은사과'
print(my_dict) # {'apple': '썩은사과', 'banana': '바나나'}

# 만약 없는 키를 제공해주면?? ==> 해당 키를 가진 값을 추가하여 준다

```

###### 딕셔너리 메서드
- d.claer()
- d.copy
- d.keys
- d.values
- d.items
- d.get()
- d.get(k, v)
- d.pop()
- d.pop(k, v)
- d.update([others])


- .get(key[,default])
key를 통해 value를 가져옴
keyError가 발생하지 않으며, default값을 설정할 수 있음(기본: None)
my_dict[key]로 가져올 경우에는 값이 없으면 error가 남

- .pop(key[,default])
key가 딕셔너리에 있으면 ㅈ거하고 해당 값을 반환
그렇지 않으면 default를 반환
default값이 없으면 error 반환

``` python
my_dict = {'apple':'사과', 'banana':'바나나'}
data = my_dict.pop('apple')
print(data, my_dict)    # 사과 {'banana': '바나나'}
data = my_dict.pop('apple', 0)
print(data)             # 0
```


- .update()
값을 제공하는 key, value로 덮어쓴다.


``` python
my_dict = {'apple':'사', 'banana':'바나나'}
my_dict.update(apple = '사과') 
print(my_dict) # {'apple': '사과', 'banana': '바나나'}



my_dict = {'apple':'사과', 'banana':'바나나'}

for key in my_dict :
    print(key) 
#apple
#banana

for value in my_dict.values() :
    print(value)

#사과
#바나나

for key, value in my_dict.items() :
    print(f'key : {key} / value: {value}') 
# key : apple / value: 사과
# key : banana / value: 바나나



```


--- 


# 얕은 복사와 깊은 복사

##### 얕은 복사: 객체의 실제 값이 아닌 참조값(주소값)을 복사하는 것
##### 깊은 복사: 참조값이 아닌 인스턴스를 새로 복사하여 아예 실제값을 복사하는 것


### 깊은 복사가 일어나는 파이썬의 자료형들

1. int
a = 1
b = a
b = 2
print(a, b) # 1  2
=> 깊은 복사

2. flaot
a = 1.0
b = a
b = 2.0
print(a, b) # 1.0  2.0
=> 깊은 복사

3. string
a = 'a'
b = a
b = 'b'
print(a, b) # a  b
=> 깊은 복사

4. boolean
a = True
b = a
b = False
print(a, b) # True False
=> 깊은 복사

### 얕은 복사가 일어나는 파이썬의 자료형들

5. list
a = [1]
b = a
b[0] = 2
print(a, b) # 2, 2
=> 얕은 복사 / 사물함만 빌려쓴 거 였는데 사물함 안의 값을 바꾸니 둘 다 바뀌어 버림

def finc(arr):
	arr[0] = 'd' # 리턴값 없이 지역변수처럼 바뀐 것인데도
tmp = ['a', 'b', 'c']

print(tmp) # ['a', 'b', 'c']
func(tmp) 
print(tmp) # ['d', 'b', 'c'] # tmp값이 변경됨



6. dictionary
a = ['key' : 'value']
b = a
b['key'] = 'b'
print(a, b) # {'key': 'b'} {'key': 'b'}
=> 얕은 복사 / 사물함만 빌려쓴 거 였는데 사물함 안의 값을 바꾸니 둘 다 바뀌어 버림


7. set
a = {1}
b = a
b.add(2)
print(a, b) # {1, 2} {1, 2}
=> 얕은 복사 / 사물함만 빌려쓴 거 였는데 사물함 안의 값을 바꾸니 둘 다 바뀌어 버림

# 수정 불가능!
8. tuple
a = (1,)
b = a
b[0] = 2
print(a, b) # Error

def change_variable(n):
	n = 'c'
	return n

def change_list(arr):
	arr[0] = 'c'

a = 'a'
a = def change_variable(a)
print(a)

a_list = ['a']






### 복사 방법
- 할당
- 얕은 복사 : 변수에 이름을 추가하는 것 (연결선만 추가해줌)
- 깊은 복사 : 이름을 추가하는 게 아니라 값 자체를 완전히 복사해서 새로운 값을 만든다


###### 할당
- 대입 연산자(=)
``` python

original_list = [1, 2, 3]

# 얕은 복사
copy_list = original_list
print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]

# 값을 수정
copy_list[0] = 'hello'
print(original_list, copy_list) # ['hello', 2, 3] ['hello', 2, 3]
# 얕은 복사를 통해 복사한 리스트들 모두가 영향을 받게 된다

```

대입 연산자(=)를 통한 복사는 해당 객체에 대한 객체 참조를 복사
해당 주소의 일부값을 변경하는 경우 이를 참조하는 모든 변수에 영향
(값을 빌리는 게 아니라, 사물함을 같이 쓰는 것 !)

###### 얕은 복사

- 얕은 복사 문제해결: slice 연산자를 활용하여 같은 원소를 가진 리스트지만 연산된 결과를 복사(다른 주소)
얕은 복사 문제를 해결할 수 있음

``` python

a = [1,2,3]
b = a[:] 
print(a, b) # [1, 2, 3] [1, 2, 3]
b[0] = 5
print(a, b) # [1, 2, 3] [5, 2, 3]

```

``` python

original_list = [1,2,3]
copy_list = original_list
print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]

copy_list[0] = 'hello'
print(original_list, copy_list) # ['hello', 2, 3] ['hello', 2, 3]


original_list = [1,2,3]
copy_list = original_list[:]
print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]

copy_list[0] = 'hello'
print(original_list, copy_list) # [1, 2, 3] ['hello', 2, 3]

```

- 얕은 복사 주의사항
: 복사하는 리스트의 원소가 주소를 참조하는 경우
``` python
a = [1, 2, ['a', 'b']]
b = a[:]

print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]

b[2][0] = 0

print(a, b) # [1, 2, [0, 'b']] [1, 2, [0, 'b']]
# 2차원 배열은 [:]으로 해결 못 함

```


###### 깊은 복사
깊은 복사를 사용하게 되면 복사 대상 리스트를 새로 만들어서 거기에 이름을 연결시킨다.

```python

import copy

a = [1, 2, ['a','b']]
b = copy.deepcopy(a) # 깊은 복사

# 통째로 복제!
print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]
b[2][0] = 0
print(a, b) # [1, 2, ['a', 'b']] [1, 2, [0, 'b']]

```

--- 


- 파이썬 인터렉티브 모드로 들어가서 오류가 나온다면: exit() 입력!
-  if __name__ == '__main__': # '실행할 때'라는 의미
	pass
