# No2    最长重复子数组

## 题目描述

给两个整数数组$A$和$B$,返回两个数组中公共、长度最长的子数组的长度。(No718)

## 暴力破解法



## 动态规划

~~~java
int lenA = A.length;//数组A的长度
int lenB = B.length;//数组B的长度
int[][] dp = int[lenA+1l][lenB+1];//动态规划矩阵
~~~

1.  如果$A[i]=B[j]$，那么$dp[i + 1][j+1] = db[i][j]+1$。
2. 如果$A[i] \neq B[j]$，那么$db[i][j] = 0$。
3. 答案为所有$db[i][j]$中的最大值。

~~~java
int max = 0;//最长子数组长度
for(int i = 1; i <= lenA; i++){
    for(int j = 1; j <= lenB ; j++){
        if(A[i-1] == B[j-1]){
            dp[i][j] = dp[i-1][j-1] + 1;
        }
		max = Math.max(pd[i][j],max);
    }
}
~~~

