# 第五天打卡

## 题目
给定一个由 整数 组成的 非空 数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

## 题目难度----简单

## 题目示例
> 输入：digits = [1,2,3]
输出：[1,2,4]
解释：输入数组表示数字 123。
> 输入：digits = [9]
输出：[1,0]
> 输入：digits = [9,9]
输出：[1,0,0]
解释：输入数组表示数字99

## 先自己，如果实在没有思路，才可以继续向下看哦！


## 解题思路
从示例来看，这道题是要给非负整数加1，但这个非负整数又表现为数组。
所以我们可以从尾部遍历数组，倒着遍历，给数组的最后一位元素+1,如果它不等于10，就跳出循环；如果等于10，就表示需要进位，当前元素等于0；循环结束，表示数组中的元素全部为9，则将首位设为1，
再尾部插入一个值为0的新元素。

## 代码
### 代码1-8ms,19MB
```
class Solution {
    function plusOne($digits) {
        for($i=count($digits)-1;$i>=0;$i--){
            $digits[$i]++;
            if($digits[$i] !=10){
                return $digits;
            }
            $digits[$i] = 0;
        }
        $digits[0] = 1;
        $digits[count($digits)] = 0;
        return $digits;
    }
}
```

### 代码2 -官方示例
```
class Solution {

    /**
     * @param Integer[] $digits
     * @return Integer[]
     */
    function plusOne($digits) {
        for ($i = count($digits)-1; $i >= 0;) {
            if ($digits[$i] != 9) {
                $digits[$i]++;
                break;
            } else {
                $digits[$i] = 0;
                $i--;
                if ($i < 0) {
                    $digits = array_merge(array(1), $digits);
                }
            }
        }
        return $digits;
    }
}
```


#### 本来想着用先把数组转化成一个整数，再+1，再将整数转化为数组。但好像失败了！ 错误代码如下,先记录一下
```
class Solution {
    function plusOne($digits) {
        $intTemp = 0;
        for($i=0;$i<count($digits);$i++){
            $intTemp = $intTemp * 10 +$digits[$i];
        }
        $intTemp = $intTemp+1;
        $digits = array_map('intval',str_split($intTemp));
        return $digits;

    }
}
```

