# 第八天打卡！

## 一、题目
给定一个非负整数 numRows，生成「杨辉三角」的前 numRows 行。

在「杨辉三角」中，每个数是它左上方和右上方的数的和。

## 二、题目难度---简单

## 三、题目示例
```
输入: numRows = 5
输出: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

输入: numRows = 1
输出: [[1]]
```

## 先自己思考，实在没有思路才可以继续向下看哦！

## 四、解题思路
杨辉三角生成规则生成。解题思路可以从一个矩阵开始，比如当整数=1时，就一个元素，元素的下标为[1,1];
当整数=2时，2个元素，元素的下标是[2,1][2,2];
整数=3时，3个元素，元素的下标是[3,1][3,2][3,3]。

## 五、代码
### 代码1
```
class Solution {

    /**
     * @param Integer $numRows
     * @return Integer[][]
     */
    function generate($numRows) {
           $result = [];
        for($i=1;$i<=$numRows;$i++){
            for($j=1;$j<=$i;$j++){
                if($j==1 || $j==$i){
                    $result[$i][$j] = 1;
                }else{
                    $result[$i][$j] = $result[$i-1][$j-1] + $result[$i-1][$j];
                }
            }
        }
        return $result;
    }
}
```
### 代码2
```
class Solution {
    function generate($numRows) {
           $arr = range(1,$numRows - 1); //用于创建一个任何类型的包含指定范围元素的数组。
           $result = [[1]];  //初始数组
           if($numRows == 1){
               return $result;  //如果只有一行就返回即可！
           }
           
           foreach($arr as $key){
               $row = [1];  //第一个元素为1 ，$key=1,2,3,4,5
               $lastRow = $result[$key-1];  //这里是个一维数组，
               $lastCount = count($lastRow); //这里统计这个一维数组中的元素值
               for($i=0;$i < $lastCount -1;$i++){
                   if(isset($lastRow[$i+1])){
                       array_push($row,$lastRow[$i]+$lastRow[$i+1]);
                   }
               }
               array_push($row,1);  //用于向一个数组的尾部添加元素，给第二个数组尾部加入一个值为1的元素
               $result[$key] = $row;
           }
           return $result;
    }
}
```
