# tibaml0315

## 物件導向

```python
# https://docs.python.org/3/reference/datamodel.html
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return "({}, {})".format(self.x, self.y)

    def __repr__(self):
        return self.__str__()

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __lt__(self, other):
        d1 = self.x ** 2 + self.y ** 2
        d2 = other.x ** 2 + other.y ** 2
        return d1 < d2

p1 = Point(3, 4)
p2 = Point(1, 2)
# print -> p.__str__()
print(p1)
# p1 == p2 -> p1.__eq__(p2)
p1 == p2
p1 in [Point(3, 4), Point(5, 6)]
# p1 > p2 -> p2.__lt__(p1)
p1 > p2
sorted([p1, p2])
```

## 瞎聊遞迴

```python
# 1~10
total = 0
for i in range(10):
    total = total + (i + 1)

def add(n):
    if n == 1:
        return 1
    else:
        ans = add(n-1) + n
        return ans
add(10)

# 合內塔
def hanoi(n):
    if n == 1:
        return 1
    else:
        return 2 * hanoi(n-1) + 1
hanoi(4)

step = 0
for i in range(3):
    step = 2 * step + 1
step


# lt 198
def rob(l):
    def helper(l, idx):
        if idx >= len(l):
            return 0
        else:
            case1 = l[idx] + helper(l, idx+2)
            case2 = helper(l, idx+1)
            return max(case1, case2)
    return helper(l, 0)
rob([5, 2, 3, 100])

l = [5, 2, 3, 100]
prev2, prev1 = l[0], max(l[0], l[1])
for i in range(2, len(l)):
    case1 = prev2 + l[i]
    case2 = prev1
    val = max(case1, case2)
    prev2, prev1 = prev1, val
print(prev1)
```

## zip/enumerate/*

```python
l = ["a", "b", "c"]
e = list(enumerate(l))
list(zip([1, 2, 3], [4, 5, 6], [7, 8, 9]))
# (0, 1, 2), ("a", "b", "c")
list(zip(*e))
```

## 一氣呵成創建

```python
# list
[i ** 2 for i in range(10)]
# set
{abs(i) for i in range(-10, 10)}
```

## 函式是種型態

```python
# 型態 + 操作
# list + [0]
# print + (3)
b = 3
b = int
b(4.2)
def t(digit=0):
    if digit == 0:
        return int
    else:
        return round
t(0)(4.6)

# 物件導向也是一樣的道理
class Person:
    pass
class SuperPerson:
    pass

def t(cond):
    if cond is True:
        return Person
    else:
        return SuperPerson
type(t(False)())
```

## decorator基本(定義裝飾)

```python
def test(f):
    print(f.__name__)
    return f
    
@test
def other():
    return 3
```

## decorator進階(定義的時候裝飾一個wrap, 你之後每次執行其實就像在執行wrap function)

```python
from functools import wraps
def test(f):
    @wraps(f)
    def wrapper(*args, **kwds):
        # 替換成你每次都想做的前置工作
        print(f.__name__)
        return f(*args, **kwds)
    return wrapper

# 跑的是
# test(other) print(other.__name) return other
@test
def other():
    return 3

@test
def another():
    return 4

print(other())
print(other())
print(another())
```

## Pandas篩選操作

```python
d = pd.DataFrame([
    [1, 2],
    [3, 4],
    [5, 6]
])
d[[True, False, True]]
```

## loc/iloc

```python
d = pd.DataFrame([
    [1, 2],
    [3, 4]
], index=[0, 0])
d.iloc[0]
d.loc[0]
```

# YOLOV4

[程式碼](https://colab.research.google.com/drive/1Kg7KQWS2vb7y1a2pjDxLdfdreBPoPGoq?usp=sharing#scrollTo=YsJ0mZeOUx4O)

[資料集](https://drive.google.com/file/d/1qUCxP2QOCRUSpOnqFM9bnh9OwFO5x3WI/view?usp=sharing)

# Transfer

[資料集](https://drive.google.com/drive/folders/1KsT58htBrvhdBKVaKSmHyTGsk3GVEJBw?usp=sharing)

# Embedding

[w2v](https://colab.research.google.com/drive/1cC0T9L6RSFw7UVJS9BmlBFvh8STuyBZD?usp=sharing)

[fasttext](https://colab.research.google.com/drive/1EVt3U7ddQUWokb-ZyZonbsPwkzl-x7O5?usp=sharing)

[Face(GPU)](https://colab.research.google.com/drive/1Fdzjw0Rh4ZzRVDvObKAskPAY4AHP-2za?usp=sharing)

[人臉辨識講義](https://colab.research.google.com/drive/1iqfxwoeUswDVKaW0mnT3Yx9nNk-GMuoH?fbclid=IwAR3aMLGvzPXnQHQOkjU06ZiDwvhtIINQb_jYfI7vVwDvBnmwM4TgBnf2lGk&usp=drive_open)
