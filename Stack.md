# Stack in Java

## What is Stack?

Stack is a **linear data structure** that follows:

> LIFO → Last In First Out

### Simple meaning:
Jo last me aata hai, wo pehle nikalta hai.

### Example:
Plate stack 🧱  
Upar wali plate pehle niklegi.

---

## Stack Syntax (Java)

```java
import java.util.Stack;

Stack<Integer> st = new Stack<>();
```

---

## Basic Methods

### 1. push()
Add element

```java
st.push(10);
st.push(20);
```

---

### 2. pop()
Remove top element

```java
st.pop();
```

---

### 3. peek()
Top element dekhna (remove nahi hota)

```java
st.peek();
```

---

### 4. isEmpty()
Check stack empty hai ya nahi

```java
st.isEmpty();
```

---

### 5. size()
Total elements

```java
st.size();
```

---

## When to Use Stack?

Stack tab use karo jab:

- Reverse karna ho
- Backtrack karna ho
- Matching check karna ho (brackets)
- Previous / Next element nikalna ho
- Undo / redo type problem ho

---

## Common DSA Patterns

### 1. Reverse Pattern

**Use case:** string / array reverse

👉 Idea:
push all → pop all

---

### 2. Valid Parentheses

**Use case:** (), {}, []

👉 Idea:
- opening → push
- closing → check top

---

### 3. Next Greater Element

**Use case:** next bigger number find karna

👉 Idea:
stack me useful elements store karo

---

### 4. Previous Greater / Smaller

👉 Idea:
stack me compare + pop useless elements

---

### 5. Monotonic Stack

Stack always:

- increasing OR
- decreasing

Used in:
- stock span
- daily temperature
- histogram

---

## How to Identify (Important)

Agar problem me ye words ho → Stack use karo:

- next / previous greater
- reverse
- brackets
- undo
- backtracking

---

## Time Complexity

| Operation | Time |
|----------|------|
| push     | O(1) |
| pop      | O(1) |
| peek     | O(1) |

---
# STEPS OR PATTERN 
## Problem Idea

We remove duplicates by using a **new container (pocket / stack)**.

Instead of comparing with previous array elements,  
we compare with the **last element in pocket**.

---

## Core Concept

We maintain a "pocket" (can be stack or list):

👉 Always compare current item with **last inserted item**

---

## Step-by-Step Thinking

For every element `arr[i]`:

### Step 1: Will this item come in answer?

Check:
- Is pocket empty? → YES → take it
- OR current != pocket.last → take it
- OR current == pocket.last → remove and remove it from pocket also

---

### Step 2: How many items to remove?

we should think is it pair or what:

```
if (arr[i] == pocket.last)
```

👉 then we remove it from stack and pocket also**


### Step 3: Should we keep this item?

Rule:

- If same as last → ❌ Delete both pocket and stack
- If different → ✅ add to pocket

---

## Pattern Name

👉 This is basically:

- Stack-based duplicate removal
- Greedy last-element checking
- “Keep only if different from last”

---

## Key Insight (VERY IMPORTANT)

> You never compare with full array  
> You only compare with **last inserted element**

This is what makes it O(n)

---
## One Line Summary

Stack = **Last In First Out + problem solving tool for reverse, backtrack, and next/prev problems**

# QUESTION AND PROBLEMS 

### 1.https://leetcode.com/problems/reverse-string/
``` java
class Solution {
    public void reverseString(char[] s) {
        Stack<Character> st = new Stack<>();
        int n = s.length;
        String res = "";
        for(int i =0; i<n; i++){
            st.push(s[i]);
        }
        int i =0;
        while (!st.isEmpty()){
            s[i++] = st.pop();
        }
    }
}
```
### 2.https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/
``` java
class Solution {
    public String removeDuplicates(String s) {
        Stack<Character> st = new Stack<>();
        int n = s.length();
    
        for(int i =0; i<n; i++){
            if (st.isEmpty()){
                st.push(s.charAt(i));
                continue;
            }
            if(st.peek()==s.charAt(i)){
                st.pop();
                continue;
            }else{
            st.push(s.charAt(i));
            }
        }
        StringBuilder res = new StringBuilder();
        while(!st.isEmpty()){
            res.append(st.pop());
        }
        return res.reverse().toString();
    }
}
```

### 3.https://leetcode.com/problems/valid-parentheses/
``` java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> st = new Stack<>();
        int i=0;
        int n = s.length();

        for ( i=0; i<n; i++){
             char ch = s.charAt(i);
            if (ch == '(' || ch == '[' || ch == '{' ){
                st.push(ch);
            }else {
                if(st.isEmpty()){
                return false;
            }
             if(
             (ch == ')' && st.peek() == '(') || 
             (ch== '}' && st.peek()== '{') ||
             (ch== ']' && st.peek()== '[') ){
                st.pop();
            } else{
                return false;
            }
        }
     }
        if(!st.isEmpty()){
            return false;
        }
        return true;
    }
}
```
### 4. https://leetcode.com/problems/next-greater-element-ii/
``` java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] ans = new int[n];
        Stack<Integer> st = new Stack<>();
        
        for(int i= 2*n-1; i >= 0; i--){
            int idx = i %n;
             
             while(!st.isEmpty() && st.peek()<=nums[idx]){
                st.pop();
             }
             if(i<n){
                if(st.isEmpty()){
                    ans[idx]= -1;
                }else {
                    ans[idx] = st.peek();
                }
             }
             st.push(nums[idx]);
        }
        return ans;
    }
}
```









