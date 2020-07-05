# No 7 数组中的第K个最大元素

**题目表述**

在未排序的数组中找到第$\boldsymbol K$个最大元素。请注意，你需要找到的是数组排序后的第$k$个最大的元素，而不是第k个不同元素。

**示例1：**

~~~java
输出：{3,2,1,5,4,6} 和 k = 2
输出: 5
~~~

**示例2：**

~~~java
输入：{3,2,3,1,2,4,5,5,6} 和 k = 4
输出： 4
~~~

**说明：**

你可以假设$k$总是有效的，且$1 \le k \le$数组的长度。

**方法一：快速排序**

**思路及算法**

1. 找到数组第k大的元素就是找到排序后数组下标为$nums.length-k$处的元素
2. 选取数组的第一个元素作为轴值，将大于轴值的元素放在轴值右边，小于等于轴值的元素放在左边。返回重新排序后轴值元素所在数组的下标$index$。
   1. 定义两个指针$left$和$right$分别指向数组的第二个元素和数组的最后一个元素；
   2. 先将$right$向左移动直到$num[right]$小于轴值，再将$left$指针向右移动，直到$nums[left]$大于轴值，此时交换两个位置处的元素；
   3. 当两个指针指向同一个元素处时（由于是$left$指针先移动），将数组的第一个元素和$nums[left]$交换，返回此时的指针$left$值，即重新排序后的轴值元素所在数组的下标。
3. 如果轴值元素的下标小于$nums.length-k$，说明要找元素在当前轴值元素对应的**右子数组**，否则在**左子树组**，选择对应的数组进行步骤2计算，直到找到轴值元素下标等于$nums.length-k$时，返回此时轴值元素，即为第$\boldsymbol K$大的元素。

**代码**

~~~java
public int findKthLargest(int[] nums,int k){
    //确定第k大元素在升序排序后的下标
    int index = nums.length - k;
    
}
//找到轴值在数组中的index
public int partition(int[] nums,int left,int right){
    int x = nums[left],index = left;
    left += 1;
    while(left<right){
        while(nums[right]<x){
            if(nums[left]>x){
                swap(nums,left,right);
            }else{
                left++;
            }
        }
        right--;
    }
    swap(nums,index,left);
    return left;
}
//辅助函数 交换两个位置的元素
public void swap(int[] nums,int left,int right){
    int temp = nums[left];
    nums[left] = nums[right];
    nums[right] = temp;
}
~~~

