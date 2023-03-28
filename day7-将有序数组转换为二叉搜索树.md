# 第八天打卡！

## 一、题目
给你一个整数数组 nums ，其中元素已经按 升序 排列，请你将其转换为一棵 高度平衡 二叉搜索树。

高度平衡 二叉树是一棵满足「每个节点的左右两个子树的高度差的绝对值不超过 1 」的二叉树。


## 二、题目难度--简单

## 三、题目示例
```
输入：nums = [-10,-3,0,5,9]
输出：[0,-3,9,-10,null,5]
解释：[0,-10,5,null,-3,null,9] 也将被视为正确答案：

输入：nums = [1,3]
输出：[3,1]
解释：[1,null,3] 和 [3,1] 都是高度平衡二叉搜索树。
```

## 四、解题思路

这道题，我自己没有什么思路，是看了别人题解，写的。写完之后，好像明白了一点，就是利用二分法，取这个升序数组的最中间的元素，作为二叉树的根节点，然后递归将左边的元素作为左子树节点，
右边的元素作为右子树的节点。

## 五、代码
### 代码1
```
class Solution {

    /**
     * @param Integer[] $nums
     * @return TreeNode
     */
    function sortedArrayToBST($nums) {
        return $this->dfs($nums,0,count($nums) - 1);
    }

    private function dfs($nums,$left,$right)
    {
        if($left > $right) return null;
        $mid = $left + round(($right-$left)/2);
        $root = new TreeNode($nums[$mid]);
        $root->left = $this->dfs($nums,$left,$mid-1);
        $root->right = $this->dfs($nums,$mid+1,$right);
        return $root;
    }
}
```
