---
title: "[Backjoon] 1016_제곱 ㄴㄴ 수 (python 파이썬 코드)"
excerpt: ""

categories:
  - Baekjoon
tags:
  - 알고리즘
  - 수학

last_modified_at: 2020-09-24T08:06:00-05:00
---

![1016_제곱 ㄴㄴ 수_1](https://user-images.githubusercontent.com/57481424/94096240-90ec2f00-fe5e-11ea-8b1e-f18feaf27c28.PNG)
![1016_제곱 ㄴㄴ 수_2](https://user-images.githubusercontent.com/57481424/94096245-921d5c00-fe5e-11ea-8737-76965bc88dd7.PNG)

<br>

```python
#초기접근 답은 나오나 시간초과함
import math
min, max = map(int, input().split())

cnt=0
for i in range(min, max+1):
    for j in range(2, i+2):
        if pow(j,2) > i:
            cnt +=1
            break
        if i%pow(j,2) == 0:
            break

print(cnt)
```

초기에 접근한 코드는 사실 적으면서 시간초과를 예상하긴했다.

min이 최대 1,000,000,000,000에 근접한 수일 경우 제일 작은 제곱수인 4부터 9, 16, 25, 36, ... 나누고 나머지를 확인하는 과정을 매우 많이 하게 된다.

그리고 예상대로 시간초과가 나와 다른 방법을 생각했다.

<br>

```python
import math
min, max = map(int, input().split())
validate = [1 for i in range(max-min+1)]
cnt=0
i=2
while i**2 <= max:
    mul = min // i**2
    while mul * (i**2) <= max:
        if mul * (i**2) - min >= 0 and mul * (i**2) - min <= max-min:
            validate[mul * (i**2) - min] = 0
        mul +=1
    i +=1

print(sum(validate))
```

에라토스테네스의 체를 활용한 코드이다.

에라토스테네스의 체란 소수인 것을 찾고, 그것의 배수들에는 모두 소수가 아니라는 표기를 해 놓아서 마치 체처럼 걸러내는 알고리즘이다.

이 문제에서는 내가 찾아봐야할 수를 리스트에 매핑해주고 가장 작은 제곱수인 4부터 4\*1, 4\*2, ... 반복해서 해당하는칸은 나누어떨어진다는 의미에서 1 -> 0으로 만들어준다.

그러면 모든 숫자에 대해 나누어 떨어지는지 살펴보지 않기 때문에 시간복잡도를 크게 낮출수있다.