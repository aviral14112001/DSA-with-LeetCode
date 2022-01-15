# *Solution 1*

## 167. Two Sum II - Input array is sorted

### Question
Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

### Approach
The function twoSum should return indices of the two numbers such that they add up to the target, where **index1** must be less than **index2**               
in order to achieve that declare *i = 0* & *j = n-1*                                                              
while **i<j** go in *&* if not then array is only one element large
if no[i]+no[j]==target return the *index+1*                                                    
else if no.[i]+no.[j] not equal to *target* 
then *--j* else *i++* and find the intended index

**Complexity: O(n)**

```
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int n = numbers.size();
        
        int i = 0, j = n-1;
        
        while(i < j){
            if(numbers[i] + numbers[j] == target){
                return {i+1, j+1};
            }else if(numbers[i] + numbers[j] > target){
                --j;
            }else{
                ++i;
            }
        }
        
        return {0,0};
    }
};
```

# *Solution 2*

## 367. Valid Perfect Square

### Question
Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note :
* Do not use any built-in library function such as *sqrt*           

### Approach
Here we are using *Binary Search Divide & Conquer* techique              
Set mid = (low+high) >> 1 (must be greater then 1)                                                              
if mid * mid == num return the *true*(we found it)                                                   
else if mid * mid < num then *low = mid +1*            
else *high = mid +1* (so basically adjust the mid) if not found return *false*       

**Complexity: O(log n)**
                                                                                                               
```
class Solution {
public:
    bool isPerfectSquare(int num) {
        long long low = 1, high = num;
        while(low <= high){
            long long mid = (low+high) >> 1;
            if(mid * mid == num){
                return true;
            }else if(mid * mid < num){
                low = mid + 1;
            }else{
                high = mid - 1;
            }
        }
        return false;
    }
};
```

# *Solution 3*

## 33. Search in Rotated Sorted Array

### Question
There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

You must write an algorithm with O(log n) runtime complexity.         

### Approach
Here we are using *Binary Search Divide & Conquer* techique OR *pivoted Binary Search*               
LeftIndex to Zero and Right to Last off the array                      
Set mid = (low+high)/1 *&* if mid is target return midIndex                             
between leftIndex and midIndex right-- *else* left++                                                    
between midIndex and rightIndex left++ *else* right-- 
(comparing the index no. = target if not adjust the values) OR *return -1*

**Complexity: O(log n)**                                                                                     
                      
```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int leftIdx = 0;
        int rightIdx = nums.size() - 1;
        
        while (leftIdx <= rightIdx) {
            int midIdx = (leftIdx + rightIdx) / 2;
            if (nums[midIdx] == target) {
                return midIdx;
            }
            if (nums[leftIdx] <= nums[midIdx]) { // left is sorted
                if (target >= nums[leftIdx] && target < nums[midIdx]) {
                    rightIdx = midIdx - 1;
                } else {
                    leftIdx = midIdx + 1;
                }
            } else { // right is sorted
                if (target > nums[midIdx] && target <= nums[rightIdx]) {
                    leftIdx = midIdx + 1;
                } else {
                    rightIdx = midIdx - 1;
                }
            }
        }
        return -1;
    }
};
```