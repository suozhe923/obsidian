## Recursion(递归)

![](../../Pictures/a1.drawio.png)
2.对于一个2x2的方格有两种平铺方式
设f(n)为方法数
2x1 : 1
2x2 : 2
2x3 : f(1) + f(2)
f(n) = f(n-1) + f(n-2) 转为斐波那契数列