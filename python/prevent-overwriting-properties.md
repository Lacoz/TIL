Python classes  allows initialization of properties inline, but this is suprisingly problematic:


```
class Grid:
    start: int
    data: dict = {}
    def __init__(self, start):
        self.start = start
        self.data = {}
    def doStep1(self, likes):
        self.data['likes'] = likes
    def doStep2(self, views):
        self.data['views'] = views

bases = [1, 10]
grid1 = Grid(bases[0])
grid1.doStep1([2,3])
grid1.doStep2([4,5])

grid2 = Grid(bases[1])
grid2.doStep1([7,8])
grid2.doStep2([9,10])

print(grid1.data)
print(grid2.data)
```
Output is: 
```
{'likes': [7, 8], 'views': [9, 10]}
{'likes': [7, 8], 'views': [9, 10]}
```

To achieve not overwriting variables move initialization of property to __init__ method:
```
class Grid:
    start: int
    data: dict 
    def __init__(self, start):
        self.start = start
        self.data = {}
    def doStep1(self, likes):
        self.data['likes'] = likes
    def doStep2(self, views):
        self.data['views'] = views
```
