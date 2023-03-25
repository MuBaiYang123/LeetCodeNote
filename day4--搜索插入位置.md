# 第四天打卡！

## 一、题目
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为 O(log n) 的算法。

## 二、题目难度----简单

## 三、示例
```
输入: nums = [1,3,5,6], target = 5
输出: 2

输入: nums = [1,3,5,6], target = 2
输出: 1

输入: nums = [1,3,5,6], target = 7
输出: 4
```

## 如果实在没有思路，才可以继续向下看哦！

## 解题思路
这道题要求时间复杂度为O(logn)就表示需要用到二分法，也就是先将数组对半，找到一个中间元素，以它为基准，判断目标元素是在它的左边还是右边，然后循环缩小区域，最终找到符合要求的位置。
或者也可以用暴力解法，循环遍历，判断数组的值是否大于等于目标值，如果是，则返回当前元素的下标，如果否，则返回数组长度。

## 代码
### 代码1--二分查找法
```
class Solution {
    function searchInsert($nums, $target) {
        $l = -1; //左指针
        $r = count($nums);//右指针
        while ($l + 1 != $r) {
            $m = floor(($r - $l) / 2) + $l;  //中间元素
            if ($nums[$m] < $target) {
                $l = $m;
            }
            else {
                $r = $m;
            }
        }
        return $r;
    }
}
```

### 代码2---暴力解法
```
class Solution {
    function searchInsert($nums, $target) {
        $numLength = count($nums);
        for($i=0;$i < count($nums);$i++){
            if($nums[$i] >= $target){
                return $i;
            }
        }
        return $numLength;
    }
}
```
