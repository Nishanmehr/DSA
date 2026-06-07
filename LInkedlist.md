## LINKED LIST
## SLOW FAST POINTER

#### https://leetcode.com/problems/happy-number/
``` Java
class Solution {
    private int fun(int n){
            int sum = 0;
            while (n>0){
                int d = n % 10;
                n = n/10;

                sum = sum+d*d;
            }
            return sum;
        }
    public boolean isHappy(int n) {
        int slow = n;
        int fast = n;

        while (fast != 1){
            slow =  fun(slow);
            fast =  fun(fast);
            fast =  fun(fast);


           if (slow == fast && slow != 1){
            return false;
           }

        }
        return true;
        
    }
}
```
### https://leetcode.com/problems/find-the-duplicate-number/
``` java

class Solution {
    public int findDuplicate(int[] nums) {
        int slow = 0;
        int fast = 0;
        
        while ( true ){
            slow = nums[slow];
            fast = nums[fast];
            fast = nums[fast];

            if (slow == fast){
                slow = 0;

                while ( slow != fast ){
                    slow = nums[slow];
                    fast = nums[fast];
                }
                return slow;
            }
        }
    }
}
```

### https://leetcode.com/problems/middle-of-the-linked-list/
``` java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast!=null && fast.next !=null){
            slow=slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
}   

```
### https://leetcode.com/problems/linked-list-cycle-ii/
``` java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;

            if (slow==fast){
                slow = head;

                while (slow!=fast){
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow;
            }
        }
       return null;
    }
}
```
### https://leetcode.com/problems/linked-list-cycle/
``` java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null){
        
        slow = slow.next;
        fast = fast.next.next ;

        if ( slow == fast){
            return true;
        }
        }
        return false;
    }
}
```

## Kadane's Algorithm
#### WHEN WE USE IT - 
Array Subarray / contigous
sum, product /
max, min / Negative elements 

#### THOUGHT PROCESS 
Suppose we have an array:

```java
[-1, 2, -3, -4, 5]
```

We need to find the maximum subarray sum.

Initially, both `bestEnding` and `ans` are set to the first element of the array:

```java
bestEnding = arr[0];
ans = arr[0];
```

`bestEnding` represents the maximum subarray sum ending at the current index.

Starting from index `1`, for each element we calculate:

* `v1 = bestEnding + arr[i]` (extend the previous subarray)
* `v2 = arr[i]` (start a new subarray from the current element)

Then we choose the better option:

```java
bestEnding = Math.max(v1, v2);
```

After updating `bestEnding`, we compare it with the overall answer found so far:

```java
ans = Math.max(ans, bestEnding);
```

At the end of the loop, `ans` contains the maximum subarray sum and is returned as the final answer.

Time Complexity: `O(n)`
Space Complexity: `O(1)`

#### PROBLEMS

##### 1. https://leetcode.com/problems/maximum-subarray/

``` java
class Solution {
    public int maxSubArray(int[] nums) {

        int i = 0;
        int n = nums.length;
       int bestending = nums[0];
       int ans = nums[0];

       for ( i =1; i<n; i++ ){
        int v1 = bestending + nums[i];
        int v2 = nums[i];
        
        bestending = Math.max(v1,v2);
        ans = Math.max (ans, bestending);
       }
        return ans;
    }
}
```
##### 2. MINIMUM SUM contiguous SUBARRAY.
``` java

class Solution {
    static int smallestSumSubarray(int a[], int size) {
        
        // your code here
        int i = 0;
        int bestending = a[0];
        int ans = a[0];
        
        for (i=1; i<size; i++){
            int v1 = bestending + a[i];
            int v2 = a[i];
            
            bestending = Math.min(v1,v2);
            ans = Math.min(ans, bestending);
            
        }
        return ans;
    }
}
```
##### 3.https://leetcode.com/problems/maximum-product-subarray/
``` java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        int i =0;
        int minending = nums[0];
        int bestending = nums[0];
        int ans = nums[0];

        for (i =1; i<n; i++){
            int v1 = minending * nums[i];
            int v2 = bestending * nums[i];
            int v3 = nums[i];

            minending = Math.min(v3,Math.min(v1,v2));
            bestending = Math.max (v3,Math.max(v1,v2));
            ans = Math.max( ans, Math.max (minending,bestending));

        }
        return ans;
    }
}

```

##### 4.https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/

``` java
class Solution {
    public int maxAbsoluteSum(int[] nums) {
        int i = 0;
        int n = nums.length;
        int maxSum = nums[0];
        int minSum = nums[0];
        int res = nums[0];

        for (i = 1; i<n; i++){
            int v1 = (maxSum + nums[i]);
            int v2 = (minSum + nums[i]);
            int v3 = nums[i];

            maxSum = Math.max(v3, Math.max(v1, v2));
            minSum = Math.min(v3, Math.min(v1,v2));

            res = Math.max(res , Math.max(Math.abs(maxSum), Math.abs(minSum)));


        }
        return Math.abs(res);

    }
}
```
##### 5. https://leetcode.com/problems/maximum-sum-circular-subarray/
``` java
class Solution {
    public int maxSubarraySumCircular(int[] nums) {
        int totalsum = 0;
        int minSum = nums[0];
        int maxSum = nums[0];
        int cminSum = nums[0];
        int cmaxSum = nums[0];
        
        for (int i =0; i<nums.length; i++){
            totalsum+=nums[i];
        }
        for (int i =1; i<nums.length; i++){

            maxSum = Math.max(nums[i], maxSum+nums[i]);
            minSum = Math.min(nums[i], minSum+nums[i]);

            cminSum = Math.min(cminSum,minSum);
            cmaxSum = Math.max(cmaxSum,maxSum);
        }
        if(cmaxSum<0){
                return cmaxSum;
            }
        return Math.max(cmaxSum,totalsum-cminSum);
    }
}
```













