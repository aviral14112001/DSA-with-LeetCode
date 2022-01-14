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
