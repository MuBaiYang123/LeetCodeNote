# 第11天打卡！

## 题目
给你一个 非空 整数数组 nums ，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

你必须设计并实现线性时间复杂度的算法来解决此问题，且该算法只使用常量额外空间。

## 题目难度---简单

## 题目示例
```
输入：nums = [2,2,1]
输出：1
示例 2 

输入：nums = [4,1,2,1,2]
输出：4
示例 3 

输入：nums = [1]
输出：1

```

## 解题思路
1、暴力解法： 寻找只出现一次的元素，可定义一个空数组，遍历数组的同时，将在这个数组result中没有的元素，存入数组，当遍历到相同元素时，就将它移除，这样最后剩下的一个元素必定是不重复的。
2、大神简单解法：
我们想到了异或运算的性质：任何一个数字异或它自己都等于0。因此，可利用这个性质获得只出现一次的元素。

## 代码
### 暴力代码
```
class Solution {

    /**
     * @param Integer[] $nums
     * @return Integer
     */
    function singleNumber($nums) {
        $result = [];
        foreach($nums as $key => $value){
            if(! isset($result[$value])){
                $result[$value] = $value;
            }else{
                unset($result[$value]);
            }
        }
        return current($result);  //返回当前被内部指针指向的数组单元的值
    }
}
```
### 异或代码
```
class Solution {
    function singleNumber($nums) {
        $result = 0;
        for($i=0;$i< count($nums);$i++){
            $result ^=$nums[$i];
        }
        return $result;
    }
}
```
