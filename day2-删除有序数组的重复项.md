
# 第二天打卡

## 题目
给你一个 升序排列 的数组 nums ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。元素的 相对顺序 应该保持 一致 。

## 先尝试着自己，如果真的完全没有思路，才可以继续往下看哦！

## 解题思路
这道题，我们可以通过建立一个指针，指向数组的第一个元素，然后遍历，依次判断之后的元素与指针所指元素是否相等，若相等则循环继续；
若不等，则指针移动一位，并将不相等的这个元素赋值给指针所指元素，最后返回指针+1；

## 代码
### 代码1
```
function removeDuplicates($arr = [0,0,1,1,1,2,2,3,3,4])
{
    $arrLength = count($arr);
    if($arrLength <2){
        return $arrLength;
    }
    $j = 0;
    for($i=1;$i<$arrLength;$i++){
        if($arr[$j] != $arr[$i]){
            $arr[++$j] = $arr[$i];
        }
    }
    return  ++$j;

}
$result = removeDuplicates();
print_r($result);
```

### 代码2
```
function removeDuplicates($arr = [0,0,1,1,1,2,2,3,3,4])
{
   $arrLength = count($arr);
    if($arrLength <2){
        return $arrLength;
    }
    $i = 0;
    $j = 1;
    while ($j < $arrLength){
        if($arr[$i] == $arr[$j]){
            $j++;
        }else{
            $i++;
            $arr[$i] = $arr[$j];
            $j++;
        }
    }
    return  $i+1;
}
$result = removeDuplicates();
print_r($result);

```

### 代码3 --这个是力扣官方给的解题思路
```
function removeDuplicates($nums = [0,0,1,1,1,2,2,3,3,4])
{
   $arrLength = count($nums);
    if($arrLength <2){
        return $arrLength;
    }
    foreach ($nums as $k=>$v){
        if($v == $nums[$k+1] && isset($nums[$k+1])){
            unset($nums[$k+1]);
            $arrLength -=1;
        }
    }
    return $arrLength ;
}
$result = removeDuplicates();
print_r($result);

```


### 第二天打卡结束，明日继续！




