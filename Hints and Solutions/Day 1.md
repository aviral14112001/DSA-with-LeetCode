# *Solution 1*

## Approach
We want to find a square root of a number ***X***                                                                                                                                 
and return the *floor(ans)* means we want to return its integer part only                                                                                                         
so we need to find a number *mid* such that    **mid\*mid == X**                                                                                                                 
to find such a number **mid** we use binary search                                                                                                                               
if we are **X** is not a perfect square then we return number such that **floor(sqrt(X))** is equal; to that number                                                               
```
int mySqrt(int x)
{
    if (x == 1)
    {
        return 1;
    }
    long long int i = 1, j = x / 2, mid;
    while (j > i)
    {
        mid = i + (j - i) / 2;
        long long int ans = mid * mid;
        if (ans == x)
        {
            return mid;
        }
        else if (ans > x)
        {
            j = mid - 1;
        }
        else
        {
            i = mid + 1;
        }
    }
    if (j * j > x)
    {
        return j - 1;
    }
    return j;
}
```
## *Solution 2*

### Approach

This is just a simple question of binary search here you have to use already defined function  ***int guess(int num)*** to check if the guessed number **m**  is greater or smaller than the picked number 
***Only difference is that here you have to given function to check conditions of the binary search***
```
 int guessNumber(int n) {
      long long   int m,i=1,j=n;
        while(j>=i)
        {
            m=i+(j-i)/2;
            if(guess(m)==0)
            {
                return m;
            }
            if(guess(m)==-1)
            {
               j=m-1; 
            }
            if(guess(m)==1) 
            {
                i=m+1;
            }
        }
        return -1;
    }
```

## *Solution 3*

### Approach

All elements before the required have the first occurrence at even index (0, 2, ..) and the next occurrence at odd index (1, 3, …). And all elements after the required elements have the first occurrence at an odd index and the next occurrence at an even index. 
1) Find the middle index, say ‘mid’.
2) If ‘mid’ is even, then compare arr[mid] and arr[mid + 1]. If both are the same, then the required element after ‘mid’ and else before mid.
3) If ‘mid’ is odd, then compare arr[mid] and arr[mid – 1]. If both are the same, then the required element after ‘mid’ and else before mid.
*[Refrence link] (https://www.geeksforgeeks.org/find-the-element-that-appears-once-in-a-sorted-array/)*

```
int singleNonDuplicate(vector<int>& nums) {
        int m,i=0,j=nums.size()-1;
        while(j>i)
        {
            m=(j+i)/2;
            if(m%2!=0)
            {
                if(nums[m]==nums[m-1])
                    i=m+1;
                else if(nums[m]==nums[m+1])
                    j=m-1;
                else 
                    return nums[m];
            }
            else 
            {
                if(nums[m]==nums[m+1])
                i=m+2;
                else if (nums[m]==nums[m-1])
                    j=m-2;
                else 
                    return nums[m];
            }
        }
        return nums[i];
    }
```



