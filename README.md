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


</body>
</html>
