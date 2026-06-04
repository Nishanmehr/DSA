## LINKED LIST

#### https://leetcode.com/problems/happy-number/
``` Javascript
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
``` javascript

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
``` javascript
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
### https://leetcode.com/problems/linked-list-cycle-ii/
``` javascript
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
### https://leetcode.com/problems/linked-list-cycle/
``` javascript
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
when we use it 
Subarray / contigous
sum /product
max/min












