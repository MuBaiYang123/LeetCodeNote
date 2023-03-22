# 题目
## 英文
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

## 题目大意
在数组中找到 2 个数之和等于给定值的数字，结果返回 2 个数字在数组中的下标。

# 示例
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1]
```

# 看到这个题目时，先尝试着自己思考和编码，如果实在没有思路，才可以继续往下看哦！

# 解题思路
> 这道题目，乍一看，我们可以采取两个循环，循环遍历数组，如果两个值相加等于目标值，则返回它们的数组下标。但这种做法，时间复杂度太高，不是很优。
> 它的最优做法的时间复杂度是O(n)
> 思路：先顺序扫描数组，对于数组中的每一个元素，在map数组中找到给定值的另一半数字，如果能找到，则直接返回2个数字的下标。如果找不到，则把这个数字存入map中，等待扫描另一半数字的时候，再取出来返回结果。

## 我的口语话描述
==我的理解是，在循环开始前先定义一个空数组，循环时，计算目标值-当前元素的值，如果这个值在map数组中存在，则直接返回两个下标，如果不存在，则将当前值的作为键，当前值的下标作为值存入数组，再继续循环。==

# 具体代码
```
function towSum($arr=[2,7,11,15],$target = 9)
{
    $map = [];
    for ($i=0;$i<count($arr);$i++){
        $another = $target - $arr[$i];
        if(isset($map[$another])){
            return [$map[$another],$i];
        }
        $map[$arr[$i]] = $i;
    }
    return -1;
}
$result = towSum();
print_r($result);
```

# 如果数组中有多个符合条件的下标，可以定义一个数组，让它返回。
```
function towSum($arr=[54,51,99,81,1,30,70],$target = 100)
{
	if(count($arr) <=0){
		return -1;
	}
    $map = [];
	$result = [];
    for ($i=0;$i<count($arr);$i++){
        $another = $target - $arr[$i];
        if(isset($map[$another])){
            $result[] =  [$map[$another],$i];
        }
        $map[$arr[$i]] = $i;
    }
    return $result;
}
$result = towSum();
print_r($result);
```

# 坚持的第一天，每日坚持，相信终能有一些收获！
