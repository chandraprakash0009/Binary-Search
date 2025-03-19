## Find minimum time to finish all jobs with given constraints

Given an array job[], where each element represents the time required to complete a specific job. There are k identical assignees available to complete these jobs, and each assignee takes t units of time to complete one unit of a job. The task is to determine the minimum time required to complete all jobs while following these constraints: 

Each assignee can only be assigned jobs that are contiguous in the given array. For example, an assignee can be assigned jobs (job[1], job[2], job[3]) but not (job[1], job[3]) (skipping job[2]).
A single job cannot be divided between two assignees. Each job must be assigned to exactly one assignee.
Examples:

Input: job[] = {10, 7, 8, 12, 6, 8}, k = 4, t = 5  
Output: 75  
Explanation: The minimum time required to finish all the jobs is 75.   
 

Assign {10} to the first assignee.  
Assign {7, 8} to the second assignee.  
Assign {12} to the third assignee.  
Assign {6, 8} to the fourth assignee.  
Maximum time taken by any assignee is (15 * 5) = 75.

Input: job[] = {4, 5, 10}, k = 2, t = 5  
Output: 50  
Explanation: The minimum time required to finish all the jobs is 50.  
Assign {4, 5} to the first assignee.  
Assign {10} to the second assignee.  
Maximum time taken by any assignee is (4 + 5) * 5 = 50.  

### Java code
```
import java.util.*;
public class Main
{
	public static void main(String[] args) {
	    Solution obj = new Solution();
	    int nums[] = {1,2,3,4,5,6,7};
            int k=4, t=5;
	    System.out.print(obj.func(nums,k,t));
	    
	}
}
class Solution {
    public int func(int[] jobs, int k, int t) {
        long sum=0;
        for(int n : jobs){
            sum+=n;
        }
        long low=1, high=sum;
        while(low<=high){
            long mid = (low+high)/2;
            //System.out.println(low + " " + high + " " + mid);
            int part = divideJobs(jobs,mid);
            if(part>k){
                low=mid+1;
            }else{
                high=mid-1;
            }
            
        }
        return ((int) low)*t ;
    }
    private int divideJobs(int nums[], long tar){
        long sum=0;
        int count=1;
        for(int i=0; i<nums.length; i++){
            if(sum+nums[i] <= tar){
                sum+=nums[i];
            }else{
                count++;
                sum=nums[i];
            }
        }
        return count;
    }
}
