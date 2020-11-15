# 483. Smalledt Good Base

<font color=red>Hard</font> `Math` `Binary Search`

For an integer n, we call k>=2 a ***good base*** of n, if all digits of n base k are 1.

Now given a string representing n, you should return the smallest good base of n in string format.

**Example 1:**
`Input: "13"`
`Output: "3`
`Explanation: 13 base 3 is 111.`

**Example 2:**
`Input: "4681"`
`Output: "8"`
`Explanation: 4681 base 8 is 11111.`

**Example 3:**
`Input: "1000000000000000000"`
`Output: "999999999999999999"`
`Explanation: 1000000000000000000 base 999999999999999999 is 11.`

**Note:**
- The range of n is [3, 10^18].
- The string representing n is always valid and will not have leading zeros.

**Analysis:**
1. It's already known that the range of ***n*** is [3, 10^18] ......**[1]**
<br>
2. The Equal Ratio Series Summation Formula: $$S_n=a_1\cfrac{1-q^n}{1-q}$$
3. In this case, the common ratio ***q*** is the good base ***k*** we are looking for. The first item $a_1$ is 1. ***m*** is the number of 1s of n base k Therefore, the equation turns into: $$n=\cfrac{k^m-1}{k-1}$$
4. With a fixed ***n***, ***k*** becomes smaller while ***m*** grows larger. 
   $n_{min}=3$ ......from **[1]**
   $\rightarrow$ $m_{min}=2$ when $k=2$......**[2]**
<br>
1. With $k_{min}=2$, ***m*** has its maximum value:
   $n=\cfrac{2^{m_{max}}-1}{2-1}$
   $\rightarrow$ $m_{max}=log_2(n+1)$ ......**[3]**
   The range of ***m*** is [2, $log_2(n+1)$]
<br>
6. Determine the range of ***k***:
   $(k+1)^{m-1} > n > k^{m-1}$
   $\rightarrow$ $k<n^{\frac{1}{m-1}}$
   $\rightarrow$ $k>n^{\frac{1}{m-1}}-1$
   $\rightarrow$ $k=int(n^{\frac{1}{m-1}})$ ......**[4]**
<br>
1. For **[4]** we know that the only candidate of ***k*** needs to be tested for a given ***m*** is $int(n^{\frac{1}{m-1}})$. We also know that the smallest base ***k*** is 2 so we can find our ***m*** must be between 2 and $log_2(n+1)$ else ***k*** is $n-1$ when $m=2$ ......**[5]**



```python
# import math
class Solution:
    def smallestGoodBase(self, n: str) -> str:
        num = int(n)
        m = int(math.log(num+1,2)) # refer [3]
        while m > 2:
            k = int(num ** (1.0 / (m - 1))) # refer [4]
            if num * (k - 1) == k ** m - 1:
                return str(k)
            m -= 1
        return str(num - 1) # refer [5]
```
