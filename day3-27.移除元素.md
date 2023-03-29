# 第三天打卡！
## 一、题目
给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

## 二、题目难度 ---简单

## 三、示例
nums = [3,2,2,3], val = 3 ，输出数组长度应该为2，因为移除了两个3元素。
输入：nums = [0,1,2,2,3,0,4,2], val = 2
输出：5, nums = [0,1,4,0,3]

## 先尝试自己思考，如果实在没有思路，才可以继续往后看哦！加油！

## 四、解题思路
这道题的思路和第二天练习题目很相似，如果真的理解了第二天的解题思路，这道题可照搬，但更简单！
具体思路：遍历数组，判断元素是否和指定的元素相等，若相等，则移除元素，并使数组长度-1。最后，返回修改后的数组长度。


## 五、代码实现
### 1. 0ms 18.8M
```
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $val
     * @return Integer
     */
    function removeElement(&$nums, $val) {
        $numsLength = count($nums);
        if($numsLength < 1){
            return $numsLength;
        }
        foreach($nums as $k=>$v){
            if($v == $val){
                unset($nums[$k]);
                $numsLength = $numsLength -1;
            }
        }
        return $numsLength;
    }
}
```
### 2. 0ms  18.9M
```
function removeElement(&$nums, $val) {
    $left = 0;
    $right = count($nums) -1;
    $count = count($nums);

    while($left <= $right){
        if($nums[$left] == $val){
            unset($nums[$left]);
            $count--;
        }
        if(isset($nums[$right]) && $nums[$right] == $val){
            unset($nums[$right]);
            $count--;
        }
        $left++;
        $right--;
    }
    return $count;
}
```

### 3. 12ms 18.8M
```
function removeElement(&$nums, $val) {
       $numsLen = count($nums);
       if($numsLen <1){
           return $numsLen;
       }
       $j = 0;
       for($i=0;$i<$numsLen;$i++){
           if($nums[$i] !=$val){
               $nums[$j] = $nums[$i];
               $j++;
           }
       }
       return $j;
    }
```
