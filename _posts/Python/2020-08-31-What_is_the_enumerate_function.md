---
title: "[Python] enumerate 함수란?"
excerpt: ""
categories:
  - Python
tags:
  - Python
 
last_modified_at: 2020-08-31T08:06:00-05:00
---

enumerate 는 열거하다라는 단어이다. 



파이썬에서는 List , Tuple , String 등 여러가지 자료형을 입력받으면 인덱스 값을 포함하는 enumerate 객체를 돌려준다.



보통 enumerate 함수는 for문과 함께 자주 사용한다. 예를들어 아래와 같이 [‘hong’, ’gil’ , ’dong’] 이라는 리스트가 있다고 할때 이것을 enumerate를 사용해 열거를 하면 다음과 같은 값이 나온다.

```python
randomlist = ['hong','gil','dong']
b = list(enumerate(randomlist))
c = dict(enumerate(randomlist))
print(b)
print(c)

'''
결과
'''
[(0, 'hong'), (1, 'gil'), (2, 'dong')]

{0: 'hong', 1: 'gil', 2: 'dong'}
```
<br>

위와 같이 인덱스와 값이 같이 출력되는 것을 알 수 있다 . 

위의 코드를 for 문을 사용한 코드는 다음과 같다

```python
a = ['hong','gil','dong']
b = []
c = {}
for i in range(len(a)) :
    b.append((i,a[i]))
    c[i] = a[i]
print(b)
print(c)

'''
결과
'''
[(0, 'hong'), (1, 'gil'), (2, 'dong')]

{0: 'hong', 1: 'gil', 2: 'dong'}
```

  <br>



for문과 enumerate 를 같이 사용해보자

```python
a = ['hong','gil','dong']
b = []
c = {}
for i,name in enumerate(a):
    b.append((i,name))
    c[i] = a[name]
print(b)
print(c)

'''
결과
'''
[(0, 'hong'), (1, 'gil'), (2, 'dong')]

{0: 'hong', 1: 'gil', 2: 'dong'}
```

<br><br>

참조 및 출처

---

> [Python enumerate 함수](https://medium.com/@hckcksrl/python-enumerate-b19ad6b94c00)

