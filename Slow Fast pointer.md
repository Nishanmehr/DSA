# LINKED LIST
## SLOW FAST POINTER

## When to Think About It

Array/Linked list/String/numbers
Ask these questions:

1. Is there a possibility of a cycle?
2. Do I need to find the middle element?
3. Can the data be viewed as nodes connected one after another?
4. Am I repeatedly moving from one position to another?
5. Can I avoid using a HashSet and achieve O(1) space?

## Pattern

slow -> 1 step
fast -> 2 steps

while(fast != null && fast.next != null){
    slow = slow.next;
    fast = fast.next.next;
}

## Common Problems

### Cycle Detection
- Linked List Cycle (LC 141)
- Circular Array Loop
- Happy Number

### Find Cycle Start
- Linked List Cycle II (LC 142)

### Find Middle Node
- Middle of Linked List (LC 876)

### Find Duplicate Number
- Find the Duplicate Number (LC 287)

## Complexity

Time: O(n)
Space: O(1)


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

 
