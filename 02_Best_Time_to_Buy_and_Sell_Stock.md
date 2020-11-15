# Best Time to Buy and Sell Stock

- 121. <font color=green>Best Time to Buy and Sell Stock</font> `Array` `Dynamic Programming`
- 122. <font color=green>Best Time to Buy and Sell Stock II</font> `Array` `Greedy`
- 309. <font color=orange>Best Time to Buy and Sell Stock with Cooldown</font>

---

## 121. Best Time to Buy and Sell Stock

<font color=green>Easy</font> `Array` `Dynamic Programming`

Say you have an array for which the $i^{th}$ element is the price of a given stock on day ***i***.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

**Example 1:**
`Input: [7,1,5,3,6,4]`
`Output: 5`
`Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5. Not 7-1 = 6, as selling price needs to be larger than buying price.`

**Example 2:**
`Input: [7,6,4,3,1]`
`Output: 0`
`Explanation: In this case, no transaction is done, i.e. max profit = 0.`

**Personal Solution**
```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        lowest_p = sys.maxsize
        max_profit = 0
        for i in range(len(prices)):
            if prices[i] < lowest_p:
                lowest_p = prices[i]
            elif prices[i] - lowest_p > max_profit:
                max_profit = prices[i] - lowest_p
        return max_profit
```

**For Reference**
```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        cmin, maxprofit = float('inf'), 0
        for price in prices:
            if price < cmin:
                cmin = price
            elif price - cmin > maxprofit:
                maxprofit = price - cmin
        return maxprofit
```

**Tips**
1. For max integer value in Python2: ***sys.maxint***
2. For max integer value in Python3: ***sys.maxsize***
3. For max float symbol in Python3: ***float('inf')***

**Next**
<font color=green>53. Maximum Subarray</font>
<font color=green>122. Best Time to Buy and Sell Stock II</font>
<font color=red>123. Best Time to Buy and Sell Stock III</font>
<font color=red>188. Best Time to Buy and Sell Stock IV</font>
<font color=orange>309. Best Time to Buy and Sell Stock with Cooldown</font>

---

## 122. Best Time to Buy and Sell Stock II

<font color=green>Easy</font> `Array` `Greedy`

Say you have an array for which the $i^{th}$ element is the price of a given stock on day ***i***.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

**Example 1:**
`Input: [7,1,5,3,6,4]`
`Output: 7`
`Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4. Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.`

**Example 2:**
`Input: [1,2,3,4,5]`
`Output:4`
`Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4. Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are engaging multiple transactions at the same time. You must sell before buying again.`

**Example 3:**
`Input: [7,6,4,3,1]`
`Output: 0`
`Explanation: In this case, no transaction is done, i.e. max profit = 0.`

**Personal Solution**
```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        profit = 0
        for i in range(len(prices) - 1):
            if prices[i+1] > prices[i]:
                profit += prices[i+1] - prices[i]
        return profit
```

**For Reference**
```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        profit = 0
        current = None
        length = len(prices)
        for index in range(length):
            nextindex = index + 1
            if current == None:
                if index >= length - 1:
                    break
                elif prices[nextindex] > prices[index]:
                    current = prices[index]
            else:
                if index >= length - 1 or prices[nextindex] < prices[index]:
                    profit = profit + prices[index] - current
                    current = None
        return profit
```

**Next**
<font color=red>Best Time to Buy and Sell Stock III</font>
<font color=red>Best Time to Buy and Sell Stock IV</font>
<font color=orange>Best Time to Buy and Sell Stock with Cooldown</font>
<font color=orange>Best Time to Buy and Sell Stock with Transaction Fee</font>

---

