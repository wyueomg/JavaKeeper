> 个人感觉动态规划是最难的，一会爬楼梯，一会兑零钱，一会又要去接雨水，炒股就不说了，还要去偷东西，哎，我太南了

![](https://cdn.nlark.com/yuque/0/2021/png/21674094/1639551516595-9b6a2bad-c55b-43e1-b172-ced36ffa96cc.png)

### [最长上升子序列_300](https://leetcode-cn.com/problems/longest-increasing-subsequence/)

> 给定一个无序的整数数组，找到其中最长上升子序列的长度。
>
> ```
> 输入: [10,9,2,5,3,7,101,18]
> 输出: 4
> 解释: 最长的上升子序列是 [2,3,7,101]，它的长度是4。
> ```

PS： 注意「子序列」和「子串」这两个名词的区别，子串一定是连续的，而子序列不一定是连续的

> https://leetcode-cn.com/problems/longest-increasing-subsequence/solution/zui-chang-shang-sheng-zi-xu-lie-dong-tai-gui-hua-2/

这种题目看懂需要看动图

```java
 public static int getLengthOfLIS(int[] nums) {

   int len = nums.length;
   if (len < 2) {
     return len;
   }

   int[] dp = new int[len];
   Arrays.fill(dp, 1);

   for (int i = 0; i < len; i++) {
     for (int j = 0; j < i; j++) {
  //当 nums[i] <= nums[j]nums[i]<=nums[j] 时： nums[i]nums[i] 无法接在 nums[j]nums[j] 之后，此情况上升子序列不成立，跳过
       if (nums[i] > nums[j]) {
         dp[i] = Math.max(dp[i], dp[j] + 1);
       }
     }
   }
   int res = 0;
   for (int i = 0; i < len; i++) {
     res = Math.max(res, dp[i]);
   }
   return res;
 }
```

> 类似问题还有，最长递增子序列的个数、俄罗斯套娃信封问题


