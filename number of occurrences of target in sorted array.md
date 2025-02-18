## number of occurrences of target in sorted array

Given a sorted array, arr[] and a number target, you need to find the number of occurrences of target in arr[]. 

Examples :  

Input: arr[] = [1, 1, 2, 2, 2, 2, 3], target = 2  
Output: 4  
Explanation: target = 2 occurs 4 times in the given array so the output is 4.  
Input: arr[] = [1, 1, 2, 2, 2, 2, 3], target = 4  
Output: 0  
Explanation: target = 4 is not present in the given array so the output is 0.  
Input: arr[] = [8, 9, 10, 12, 12, 12], target = 12  
Output: 3  
Explanation: target = 12 occurs 3 times in the given array so the output is 3.  

## APPROACH -

FIND OUT THE FIRST AND LAST OCCURANCE OF TARGET ELEMENT IN ARRAY AND RETURN LAST-FIRST+1;  

JAVA CODE -
```

class Solution {
    int countFreq(int[] arr, int target) {
        // code here
        int left = leftIndex(arr, target);
        if(left==-1){
            return 0;
        }
        int right = rightIndex(arr,target);
        return right-left+1;
    }
    private int leftIndex(int nums[], int t){
        int low=0, high=nums.length-1;
        int idx=-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid]==t){
                idx=mid;
                high=mid-1;
            }else if(nums[mid]<t){
                low=mid+1;
            }else{
                high=mid-1;
            }
        }
        return idx;
    }
    private int rightIndex(int nums[], int t){
        int low=0, high=nums.length-1;
        int idx=-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid]==t){
                idx=mid;
                low=mid+1;
            }else if(nums[mid]<t){
                low=mid+1;
            }else{
                high=mid-1;
            }
        }
        return idx;
    }
}

