# 调试样例

回顾 W2 课内的第三道编程题“黑洞数”。

## 题面

黑洞数也称为陷阱数，又称“Kaprekar 问题”，是一类具有奇特转换特性的数。

任何一个各位数字不全相同的三位数，经有限次“重排求差”操作，总会得到 495。最后所得的 495 即为三位黑洞数。所谓“重排求差”操作即组成该数的数字重排后的最大数减去重排后的最小数。（6174 为四位黑洞数。）

例如，对三位数 207：

第1次重排求差得：720 - 27 = 693；

第2次重排求差得：963 - 369 = 594；

第3次重排求差得：954 - 459 = 495；

以后会停留在 495 这一黑洞数。如果三位数的 3 个数字全相同，一次转换后即为 0。

任意输入一个三位数，编程给出重排求差的过程。

### 输入格式：
输入在一行中给出一个三位数。

### 输出格式：
按照以下格式输出重排求差的过程：

```
序号: 数字重排后的最大数 - 重排后的最小数 = 差值
```

序号从1开始，直到495出现在等号右边为止。

### 输入样例：
```
123
```

### 输出样例：
```
1: 321 - 123 = 198
2: 981 - 189 = 792
3: 972 - 279 = 693
4: 963 - 369 = 594
5: 954 - 459 = 495
```

代码长度限制：16 KB

时间限制：400 ms

内存限制：64 MB

## 样例代码

!!! warning "注意，以下的代码是有错的，我们希望进行 debug"

```c
#include <stdio.h>

int main() {
    int x;                      //  a 3-digit number
    scanf("%d", &x);

    int iters = 1;              //  iteration count

    while (x && x != 495) {     //  495 is the magic number
        int d0 = x % 100;       //  digit 0, 10^0, unit's digit
        int d1 = x / 10 % 10;   //  digit 1, 10^1, ten's digit
        int d2 = x / 100;       //  digit 2, 10^2, hundred's digit

        int max = d0;           //  max digit
        int min = d1;           //  min digit
        int mid = d2;           //  middle digit

        if (d1 > d0) {
            max = d1;
            min = d0;
        }   //  default: d1 <= d0, max = d0, min = d1

        if (d2 > max) {
            mid = max;
            max = d2;
        }   //  default: d2 <= max, mid = d2 (can < min)

        if (min > mid) {
            int tmp = min;
            min = mid;
            mid = tmp;
        }   //  default: min <= mid, unnecessary to swap
        
        x = 99 * (max - min);   //  next number
        printf (
            "%d: %d - %d = %d\n",
            iters, 
            100 * max + 10 * mid + min,
            100 * min + 10 * mid + max,
            x
        );
        iters++;
        //  if maxd = mind = midd, x = 0, loop ends
    }

    return 0;
}
```

!!! info "当然，在变量的设计等方面这段代码可以再进行更多优化，不过在此就不详细讨论了"

先简单解释一下算法思想。`d0, d1, d2` 分别是三位数的个位、十位、百位，`max, mid, min` 分别是三个数位中最大的、居中的和最小的，`iter` 为迭代次数。每轮迭代更新 `x`，使用的公式为

$$
\begin{aligned}
    x &= (100\cdot max + 10\cdot mid + min) - (100\cdot min + 10\cdot mid + max)\\
    &= 99\cdot (max - min)
\end{aligned}
$$

按照黑洞数的要求，循环的中止条件为 495。另外，当 `x=0` 时，可知对应 `max=min=mid`，即三个数位都相同，应当中止。

中间的三个 if 语句 (18-32 行) 用途是对 `d0, d1, d2` 进行排序，从而得到 `max, mid, min`。对 `max, mid, min` 初始化为 `d0, d2, d1`，这样只有必要时才修改初始化的默认值，可以省去 else 语句。例如第一个 if 语句，只有 `d1 > d0` 时才有必要修改初始化的默认值。

程序编译运行之后，发现死循环。输出为
```
...
7688: 5495 - 1040 = 4455
7689: 5945 - 995 = 4950
...
```

## printf 大法

## VSCode 调试插件
