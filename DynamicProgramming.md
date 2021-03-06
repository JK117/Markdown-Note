# Dynamic Programming 动态规划

动态规划是编程解题的一种重要手段。1951年美国数学家R.Bellman等人根据一类多阶段问题的特点，把多阶段决策问题换为一系列互相联系的单阶段问题，然后逐个加以解决。与此同时，他提出了解决这类问题的“最优化原理”，从而创建了解决最优化问题的一种新方法：动态规划。

动态规划算法通常用于求解具有某种最优性质的问题。在这类问题中，可能会有许多可行解。每个解都对应于一个值，我们希望找到具有最优解的值。

我们可以用一个表来记录所有已解的子问题的答案。不管该子问题以后是否会被用到，只要它被计算过，节将其结果填入表中。这就是动态规划的基本思路。具体的动态规划算法多种多样，但它们具有相同的填表格式。

## 动态规划基本概念
- **阶段：** 把所有问题的求解过程恰当地分成若干个相互联系的阶段，以便于求解。过程不同，阶段数就可能不同。描述阶段的变量称为阶段变量，常用k表示。阶段的划分，一般是根据时间和空间的自然特征来划分，但要便于把问题的过程转化为多阶段决策的过程。
- **状态：** 状态表示每个阶段开始面临的自然状况或客观条件（不可控因素）。通常一个阶段由若干个状态，状态通常可以用一个数组来表示，称为状态变量。
- **决策：** 表示当过程处于某一个阶段的某个状态时，可以做出不同的决定，从而确定下一阶段的状态，这种决定称为决策。不同的决策对应着不同的数值，描述决策的变量称为决策变量。
- **状态转移方程：** 动态规划中本阶段的状态往往是上一个阶段的状态和上一个阶段的决策的结果，由第i段的状态f(i)，和决策u(i)来确定第i+1段的状态。状态转移表示为F(i+1)=T(f(i),u(i))，称为状态转移方程。
- **策略：** 各个阶段决策确定后，整个问题的决策序列就构成了一个策略，对每个实际问题，可供选择的策略有一定范围，称为允许决策集合。允许决策集合中达到最优效果的策略称为最优策略。

## 动态规划满足条件
- **最优化原理：** 最优策略的子策略也是最优的。
- **无后效性：** 某阶段状态给定后，这个阶段以后过程的发展不受这个阶段以前各个状态的影响。

---

**例题1：** 从坐下(1,1)出发，到右上(n,n)结束，走到一个点(i,j)会消耗一定体力a(i,j)，方向只能是向右或者向上，求到达目的地的最小开销。
| 5 | 4 | 3（End） |
| :-: | :-: | :-: |
| 6 | 2 | 5 |
| 0(Start) | 3 | 4 |
从一个点到下一个点只有两种方式：
- (i-1, j) -> (i, j)
- (i, j-1) -> (i, j)
从哪个点走到(i, j)就是一种决策，用dp(i, j)来代表走到一个点(i, j)消耗的最少体力：

```cpp
int a[100][100]; // a数组代表走到点(i,j)花费的体力
int dp[100][100]; // dp数组代表走到点(i,j)一共花费的最少体力
dp[1][1] = 0;
for (int i = 1; i <= n; ++i) {
    for (int j = 1;j <= n; ++j) {
        if (i == 1 && j == 1) {
            continue;
        } else if (i == 1) { //边界点
            dp[i][j] = dp[i][j-1] + a[i][j];
        } else if (j == 1) { //边界点
            dp[i][j] = dp[i-1][j] + a[i][j];
        } else {
            dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + a[i][j]; //转移方程
        }
    }
}
```

---

**例题2：** 有n个人需要在晚上过河，桥每次只允许最多两个人通过。他们只有一个手电筒，每次过桥后需要有人把手电筒带回来。第i人过桥时间为a[i]，两个人一起过桥花费的时间为两者中较长的时间。问所有人过桥需要的最短时间。
将a[i]重新递增排序，假设前i个人过河花费的最少时间m[i]，需要考虑两种情况：
- 前i-1个人已经过河，还剩一个人，让花费时间最少的人吧手电筒送过来，和第i人一起过河：m[i]=m[i-1]+a[1]+a[i]
- 前i-2个人已经过河，还剩两个人，让花费时间最少的人把手电筒送过来，第i人和第i-1人一起过河，再让花费时间次少的人送手电筒，接回花费时间最少的人：m[i]=m[i-2]+a[1]+a[i]+2\*a[2]

```python
def cross_river():
    time_cost = [1, 2, 3, 4, 7, 8]
    opt = [0]

    for i in range(1, len(time_cost)):
        if i == 1:
            opt.append(time_cost[1])
        else:
            opt.append(min(opt[i - 1] + time_cost[0] + time_cost[i],
                           opt[i - 2] + time_cost[0] + time_cost[i] + 2 * time_cost[1]))

    print(opt[-1])
```