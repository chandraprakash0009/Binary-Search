## Find nth root of m
You are given 2 numbers n and m, the task is to find n√m (nth root of m). If the root is not integer then returns -1.

Examples :

Input: n = 2, m = 9
Output: 3
Explanation: 32 = 9

Input: n = 3, m = 9
Output: -1
Explanation: 3rd root of 9 is not integer.

Input: n = 1, m = 14
Output: 14

Constraints:
1 <= n <= 30
1 <= m <= 109

APPROACH :- WE AREE GIVEN A NUMBER "M". WE HAVE TO FIND A INTEGER NUMBER X SUCH THAT X^n IS EQUAL TO M.
            SO IF N==1 THEN RETURN THE M
            LOW=1, HIGH=M/2
            IF MID^N==M THEN RETURN MID
            IF IT IS LESS THEN GO FOR RIGHT ELSE GO IN LEFT;
IF ANY INTEGER IS NOT FOUND THEN RETURN -1;

JAVA CODE:
```
class Solution {
    public int nthRoot(int n, int m) {
        // code here
        if(n==1){
            return m;
        }
        int low=1, high=m/2;
        while(low<=high){
            int mid=(low+high)/2;
            int ans =(int) Math.pow(mid,n);
            if(ans==m){
                return mid;
            }else if(ans<m){
                low=mid+1;
            }else{
                high=mid-1;
            }
        }
        return -1;
    }
}
