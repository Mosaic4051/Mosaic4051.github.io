<!DOCTYPE html>
<html>
<head>
<title>我个人的python杂货铺</title>
</head>
<body>

<h1>胡开明 3200100425 5# 药学2002 </h1>
<p>人生苦短，我学python</p>

<p>
        一、作品名称：《数列求和库》，难度***<br>
        数列描述：<br>
        求n个a的数列和。<br>
        题目来源：教材习题第六章<br>
        三、编程题<br>
        1. 使用函数求特殊数列和。给定两个均不超过9的正整数 a 和 n，要求编写函数 fn(a, n) 求 a+aa+aaa+…+aa…aa(n个a)之和，fn须返回的是数列和。<br>
        代码对应的Python知识点：<br>
        方法一：定循环与不定循环<br>
        方法二：函数：自定义、内部、匿名函数<br>
        方法三：类<br>
        源码注释：<br>
    </p>

    <p>方法一：定循环和不定循环</p>
    <pre>
#定循环 for
a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
# 初值
sum_sequence = 0
number_str = ""
# 循环
for i in range(n):
    number_str += a  # 构建数列中的每一项
    sum_sequence += int(number_str)
# 输出
print("Sum of the sequence:", sum_sequence)

# 不定循环 while
a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
sum_sequence = 0
number_str = ""
i = 0
while i < n:
    number_str += a
    sum_sequence += int(number_str)
    i += 1
print("Sum of the sequence:", sum_sequence)
    </pre>

    <p>方法二：函数实现</p>
    <pre>
# 内建函数如 sum() 结合列表推导式来求解
a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
# 使用 sum 函数和列表推导式
sum_sequence = sum([int(a * (i + 1)) for i in range(n)])
print("Sum of the sequence:", sum_sequence)

# 自定义函数 def 结合定循环
def sum_sequence_for(a, n):
    sum_sequence = 0
    number_str = ""
    for i in range(n):
        number_str += a
        sum_sequence += int(number_str)
    return sum_sequence

a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
print("Sum of the sequence:", sum_sequence_for(a, n))

# 递归函数
def sum_sequence_recursive(a, n, current_term="", sum_sequence=0):
    if n == 0:
        return sum_sequence
    current_term += a
    sum_sequence += int(current_term)
    return sum_sequence_recursive(a, n - 1, current_term, sum_sequence)

a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
print("Sum of the sequence:", sum_sequence_recursive(a, n))

# 匿名函数
from functools import reduce
a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
# 构建数列并计算和
# 使用 map 函数来构建数列，然后使用 reduce 来计算这个数列的和。
# reduce 函数在 Python3 中位于 functools模块中，需要导入使用
sum_sequence = reduce(lambda x, y: x + y, map(lambda i: int(a * (i + 1)), range(n)))
print("Sum of the sequence:", sum_sequence)
    </pre>

    <p>方法三：类实现</p>
    <pre>
class SequenceSum:
    def __init__(self, a, n):
        self.a = a
        self.n = n

    def sum_sequence(self):
        sum_seq = 0
        number_str = ""
        for i in range(self.n):
            number_str += self.a
            sum_seq += int(number_str)
        return sum_seq

# 使用示例
a = input("Enter a number: ")
n = int(input("Enter the number of terms: "))
seq_sum = SequenceSum(a, n)
print("Sum of the sequence:", seq_sum.sum_sequence())
    </pre>

 <p>
        二、作品名称：计算奇数分之一序列前n项和，难度**<br>
        数列描述：<br>
        计算序列 1 + 1/3 + 1/5 + ... 的前N项之和。<br>
        题目来源：浙大版《Python 程序设计》题目集 第2章-5 求奇数分之一序列前N项和<br>
    </p>
    <p>
        2.5 计算序列 1 + 1/3 + 1/5 + ... 的前N项之和。<br>
        输入格式:<br>
        输入在一行中给出一个正整数N。<br>
        输出格式:<br>
        在一行中按照“sum = S”的格式输出部分和的值 S，精确到小数点后6位。题目保证计算结果不超过双精度范围。<br>
        代码对应的Python知识点：<br>
        方法一：定循环与不定循环<br>
        方法二：函数：自定义、内部<br>
    </p>

    <p>方法一：用 for 构建定循环：</p>
    <pre>
n=int(input())  # 代表输入一个正整数n
b=0  # b代表每次所加的项
s=0  # s 代表序列和，sum为内置函数，不可作为变量名
#for 循环：
for i in range(1, n+1):
    # 当n是一个正整数时，i的取值将是所有1到n（包括1和n）的整数
    b=1/(2*i-1)
    s=s+b
# 输出
print("sum = {:.6f}".format(s))
    </pre>

    <p>方法二：用 while 构建不定循环：</p>
    <pre>
N=int(input())  # 代表输入一个正整数N
b=0  # b代表每次所加的项
s=0  # s 代表序列和sum，因为防止与序列和重复暂且表达为s
# while 循环：
i=1
while i <= N:
    s += 1 / (2 * i - 1)
    i += 1
# 输出
print("sum = {:.6f}".format(s))
    </pre>

    <p>小测中出现过此题变体，要求用 ceil 函数返回其近似值（整数），解答摘录如下：</p>
    <p>方法三（拓展）：构建自定义函数，用 while 构建不定循环，用 math.ceil 取整</p>
    <pre>
# ceil 函数属于 math 库，此处需引用：
import math

# 输入
N = int(input())

# 使用函数和 while 循环计算并打印结果
# 函数：
def sum(N):
    sum = 0.0
    i = 1
    # while 循环
    while i <= N:
        sum += 1 / (2 * i - 1)
        i += 1
    # 使用 math.ceil 计算大于等于总和的最小整数
    sum = math.ceil(sum)
    return sum

print(f"sum ≈ {sum(N)}")
    </pre>
</body>
</html>
