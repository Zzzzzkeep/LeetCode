# No 6 长度最小子数组

**题目表述**

给定一个含有$\boldsymbol n$ 个正整数的数组和一个整数$\boldsymbol s$，找出该数组中满足其和$\ge \boldsymbol s$的长度最小的子数组，并返回其长度。如果不存在符合条件的子数组，返回0。

**示例**

~~~java
输入：s = 7,nums = {2,3,1,2,4,3}
输出：2
解释：子数组{4,3}是该条件下的长度最小的子数组。
~~~

**进阶**A

- 如果你已经完成$O(n)$时间复杂度的解法，请尝试$O(nlogn)$时间复杂度的解法。

**方法一：双指针法**

**思路及算法**

定义两个指针$start$和$end$，它们分别表示子数组开始的位置和结束的位置，变量$sum$存放子数组中元素的和（即从$nums[start]$到$nums[end]$的元素和）。

初始状态如下

~~~java
int start = 0, end = 0;
int sum = 0;
int ans = Integer.MAX_VALUE;
~~~

移动指针$end$直到$sum \ge \boldsymbol s$，则更新子数组的最小长度。

如果$sum \ge \boldsymbol s$，保持指针$end$不变，将$start$指针向前移动一位，重新计算$sum$是否满足条件，如果满足条件则更新子数组长度，不满足条件则$end$指针向前移动一位。

**代码**

~~~Java
public int minSubArrayLen(int s,int[] nums){
    int n = nums.length;//数组长度
    //特殊情况
    if(n == 0){
        return 0;
    }
    //正常情况
    while(end<n){
        //end指针小于数组长度
        sum += nums[end];
        //如果sum大于s 移动start指针
        while(sum >= s){
            ans = Math.min(ans,end-start+1);//最小子数组长度的更新
            sum -= nums[start];
            start++;
        }
        end++;
    }
    return ans == Integer.MAX_VALUE ? 0 : ans;
}
~~~

