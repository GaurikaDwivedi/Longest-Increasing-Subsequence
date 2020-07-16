# Longest-Increasing-Subsequence Leetcode
Longest Increasing Subsequence 3 methods for solving in python

![image](https://user-images.githubusercontent.com/58950467/87664263-92281e00-c782-11ea-83a7-9492ef4f6b44.png)
```
Method 1:
Solution based on Narsimha karumanchi's 
Dynamic Programming 
Time Complexity: O(n<sup>2</sup>)
Space Complexity: O(n)
```
```
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if not nums:
            return 0
        max_len=1
        dp=[1]*len(nums)
        for i in range (len(nums)):
            for j in range (0,i):
                if nums[i]>nums[j] and dp[i]<dp[j]+1:
                    dp[i]=dp[j]+1
            max_len=max(max_len,dp[i])    
        return max_len 
```        
     
```
Method 2:
DP+ Binary Search 
Time Complexity: O(nlogn)
Space Complexity: O(n)
```
```
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if not nums:
            return 0
        
        dp=[]
        dp=[nums[0]]
        len_dp=1
        for i in range (1,len(nums)):  
            left,right=0,len(dp)-1
            while (left<right):
                mid=(left+right)//2
                if dp[mid]<nums[i]:
                    left=mid+1
                else :
                    right=mid
            if  dp[left]<nums[i] :
                dp.append(nums[i])
                len_dp+=1
            else:
                dp[left]=nums[i]
        return len_dp 
```
```
Method 3:
Tailing Method
Time Complexity: O(n)
```
```
def lengthOfLIS(self, nums):
    tails = [0] * len(nums)
    size = 0
    for x in nums:
        i, j = 0, size
        while i != j:
            mid = (i + j) / 2
            if tails[mid] < x:
                i = mid + 1
            else:
                j = mid
        tails[i] = x
        size = max(i + 1, size)
    return size
```    
    
