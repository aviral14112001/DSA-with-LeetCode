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

## 367. Valid Perfect Square

### Question
Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note :
* Do not use any built-in library function such as sqrt           

### Approach

                                                                                                               
```
class Solution {
public:
    bool isPerfectSquare(int num) {
        long left = 0, right = num;
        while (left <= right) {
            long mid = left + (right - left) / 2, t = mid * mid;
            if (t == num) return true;
            else if (t < num) left = mid + 1;
            else right = mid - 1;
        }
        return false;
    }
};
```