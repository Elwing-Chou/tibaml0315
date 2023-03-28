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
