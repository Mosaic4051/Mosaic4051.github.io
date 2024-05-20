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

    <p>
        三、作品名称：求交错序列前N项和，难度**<br>
        数列描述：<br>
        输入正整数N，求数列的前N项和，并保留三位小数<br>
        题目来源：浙大版《Python 程序设计》题目集 第2章-6 求交错序列前N项和<br>
    </p>
    <p>
        2.6 本题要求编写程序，计算交错序列 1-2/3+3/5-4/7+5/9-6/11+... 的前N项之和。<br>
        输入格式:<br>
        输入在一行中给出一个正整数N。<br>
        输出格式:<br>
        在一行中输出部分和的值，结果保留三位小数。<br>
        代码对应的Python知识点：<br>
        方法一、二：定循环、循环else结构<br>
        方法二：列表<br>
    </p>

    <p>方法一：用 for 构建定循环；用 else 语句完成分类处理</p>
    <pre>
# 输入：
n=int(input())
a=0  # a代表数列和
# 循环
for i in range(1, n+1):
    if i%2==1:
        a = a + i/(2*i-1)
    else:  # else结构
        a = a - i/(2*i-1)
# 输出，{:.3f} 代表要求的结果保留三位小数
print("{:.3f}".format(a))
    </pre>

    <p>方法二：用 if/else 创建列表，列表求和</p>
    <pre>
# 输入
n=int(input())
# 创建列表
alist=[i/(2*i-1) if i%2==1 else -i/(2*i-1) for i in range(1, n+1)]
# 列表求和：
result=sum(alist)
# 输出
print("{:.3f}".format(result))
    </pre>

     <p>
        四、作品名称：求整数段和，难度**<br>
        数列描述：<br>
        给定两个整数A和B，输出从A到B的所有整数以及这些数的和。<br>
        题目来源：浙大版《Python 程序设计》题目集 第2章-14 求整数段和<br>
    </p>
    <p>
        2.14 给定两个整数A和B，输出从A到B的所有整数以及这些数的和。<br>
        输入格式：<br>
        输入在一行中给出2个整数A和B，其中−100≤A≤B≤100，其间以空格分隔。<br>
        输出格式：<br>
        首先顺序输出从A到B的所有整数，每5个数字占一行，每个数字占5个字符宽度，向右对齐。最后在一行中按Sum = X的格式输出全部数字的和X。<br>
        代码对应的Python知识点：<br>
        创建字符串列表<br>
        定循环 for/else 结构<br>
    </p>

    <pre>
# 输入两个整数，用 map(int, input().split()) 将空格分开成字符串列表，并将字符串转换为整数
A, B = map(int, input().split())
# 初始化两个变量，s 和 c 都为0。其中 s 将用于累加求和，c 用于计数，以便每五个数字打印一行
s = c = 0
# for 构建定循环，迭代到 A、B 之间每一个整数
for i in range(A, B + 1):
    print(f'{i:5d}', end='')
    # 这行代码用于格式化打印整数 i，并且每个整数占用宽度为 5 的固定空间。end='' 参数确保数字间不会自动换行。
    # 累加求和：
    c += 1
    if c == 5:
        print()
        c = 0
    s += i
# 处理最后一行不足 5 个的情况
if c:
    print()
# 输出结果
print(f'Sum = {s}')
    </pre>
     <p>
        五、作品名称：统计素数并求和，难度***<br>
        数列描述：<br>
        本题要求统计给定整数M和N区间内素数的个数并对它们求和。<br>
        题目来源：浙大版《Python 程序设计》题目集 第4章-2 统计素数并求和<br>
    </p>
    <p>
        4.2 本题要求统计给定整数M和N区间内素数的个数并对它们求和。<br>
        输入格式:<br>
        输入在一行中给出两个正整数M和N（1≤M≤N≤500）。<br>
        输出格式:<br>
        在一行中顺序输出M和N区间内素数的个数以及它们的和，数字间以空格分隔。<br>
        代码对应的Python知识点：<br>
        导入数学库<br>
        函数自定义<br>
        for循环<br>
    </p>

    <pre>
# 导入数学库
import math

# 自定义函数作为判别数字是否是素数的依据
def is_prime(num):
    sqrt_num = int(math.sqrt(num))
    if num == 1:
        return False
    for i in range(2, sqrt_num + 1):
        if num % i == 0:
            return False
    return True

# 输入
m, n = map(int, input().split())  # m, n 为输入值
counts = 0  # counts 表示对素数的计数
sum = 0  # 初始化求和变量

# for 循环遍历 m~n 所有整数并判断是否为素数
for i in range(m, n + 1):
    if is_prime(i):
        counts += 1
        sum += i

# 输出
print(f"{counts} {sum}")
    </pre>
</body>
</html>
