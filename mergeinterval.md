# MERGE INTERVALS 
## When to Think About This Pattern?
If the problem contains:
- Intervals `[start, end]`
- Meeting timings
- Calendar events
- Time slots
- Ranges
- Overlapping segments
- and some keywords in question  conflict , merge, freetime, simultaneous usage 
rooms , load ,cpu , meeting

Think:
> "Do I need to merge overlapping intervals?"
---

# Core Thought Process

Suppose we have two intervals:

```text
[start1, end1]
[start2, end2]
```

Example:

```text
[1,5] here start1=1 ,end1=5
[3,8] here start2=3, end2=8
```

Visualize:

```text
1------5
   3--------8
```

Since the second interval starts before the first interval ends:

```text
start2 <= end1
```

```text
3 <= 5
```

They overlap ✅

Merge them:

```text
[start1, max(end1, end2)]
```

```text
[1,8]
```

---

# Golden Rule

Two intervals overlap if:

```text
start2 <= end1
```

### Overlap Example

```text
[1,5]
[3,8]
```

```text
3 <= 5
```

Overlap ✅

---

### No Overlap Example

```text
[1,5]
[7,9]
```

```text
7 > 5
```

No Overlap ❌

---

# Why Do We Sort?

Before checking overlap, sort intervals by start time.

```java
Arrays.sort(intervals, (a,b) -> a[0] - b[0]);
```

After sorting:

```text
start1 <= start2 <= start3 ...
```

Now we only need to compare:

```text
start2 with end1
```

---

# Generic Thought Process

For every interval:

```text
[start1, end1]  -> Last interval in answer

[start2, end2]  -> Current interval
```

### Case 1: Overlap

```text
start2 <= end1
```

Merge:

```text
newStart = start1
newEnd = max(end1, end2)
```

---

### Case 2: No Overlap

```text
start2 > end1
```

Add current interval separately.

---

# Example

Input:

```text
[1,3]
[2,6]
[8,10]
[15,18]
```

---

Compare:

```text
[1,3]
[2,6]
```

```text
2 <= 3
```

Overlap

Merge:

```text
[1,6]
```

---

Compare:

```text
[1,6]
[8,10]
```

```text
8 > 6
```

No overlap

Answer:

```text
[1,6]
[8,10]
```

---

Compare:

```text
[8,10]
[15,18]
```

```text
15 > 10
```

No overlap

Final Answer:

```text
[1,6]
[8,10]
[15,18]
```

---

# Template

```java
Arrays.sort(intervals, (a,b) -> a[0] - b[0]);

List<int[]> ans = new ArrayList<>();

ans.add(intervals[0]);

for(int i = 1; i < intervals.length; i++){

    int[] current = intervals[i];
    int[] last = ans.get(ans.size()-1);

    int start1 = last[0];
    int end1 = last[1];

    int start2 = current[0];
    int end2 = current[1];

    if(start2 <= end1){

        last[1] = Math.max(end1, end2);

    }else{

        ans.add(current);
    }
}
```

---
Think:
```text
1. Sort by start time
2. Take two intervals

   [start1, end1]
   [start2, end2]

3. Check:

   start2 <= end1 ?

4. Yes  -> Merge
5. No   -> Add separately
```

---

# One-Line Formula

```text
Sort → Check (start2 <= end1) → Merge or Add
```

## Q1.Meeting Rooms II
``` java
class Solution {
    public int minMeetingRooms(int[] start, int[] end) {
        // code here
        Arrays.sort(start);
        Arrays.sort(end);
        int room = 0;
        int res =0;
        int i =0;
        int j =0;
        while(i<start.length && j<end.length){
            if(start[i]<end[j]){
                room++;
                res=Math.max(res,room);
                i++;
            }else{
                room--;
                j++;
            }
        }
        return res;
    }
}
```

