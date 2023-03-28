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
