# 第10天打卡

## 题目
给定一个数组 prices ，它的第 i 个元素 prices[i] 表示一支给定股票第 i 天的价格。

你只能选择 某一天 买入这只股票，并选择在 未来的某一个不同的日子 卖出该股票。设计一个算法来计算你所能获取的最大利润。

返回你可以从这笔交易中获取的最大利润。如果你不能获取任何利润，返回 0 

## 题目难度---简单

## 题目示例---
```
输入：[7,1,5,3,6,4]
输出：5
解释：在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格；同时，你不能在买入前卖出股票。
     
输入：prices = [7,6,4,3,1]
输出：0
解释：在这种情况下, 没有交易完成, 所以最大利润为 0。
```

## 解题思路
可以先假设第一天买入股票，然后遍历数组，在其中找比第一天买入股票更低的价格，同时计算股票利润，选择最大的利润返回。


## 代码

```
class Solution {
    function maxProfit($prices) {
        $buy = $prices[0];
        $profit = 0;
        for($i=1;$i<=count($prices);$i++){
            if($prices[$i] < $buy){
                $buy = $prices[$i];
            }
            $profit = $profit > ($prices[$i]-$buy) ? $profit : $prices[$i]-$buy;
        }
        return $profit;
    }
}

或者：
class Solution {
    function maxProfit($prices) {
        $min = $prices[0];
        $max= 0;
        foreach($prices as $key=>$value){
            $min = $min > $value ? $value : $min;
            $max = $max > ($value-$min) ? $max:$value-$min;
        }
        return $max;
    }
}
```
