# 📘 04_StringBuilder.md

> **Topic:** Java StringBuilder  
> **Level:** Beginner → Advanced  
> **Author:** Nishant Mehra DSA Notes

---

# 📑 Table of Contents

1. Introduction
2. Why StringBuilder?
3. String vs StringBuilder
4. Internal Working
5. Creating StringBuilder
6. Methods
7. Capacity
8. Capacity Expansion
9. Time Complexity
10. Common Mistakes
11. Interview Questions
12. Cheat Sheet
13. Practice Questions

---

# 1. Introduction

`StringBuilder` is a mutable sequence of characters.

Unlike `String`, its contents **can be modified without creating a new object**.

## Syntax

```java
StringBuilder sb = new StringBuilder();
```

---

# 2. Why StringBuilder?

Consider this code:

```java
String s = "";

for(int i=1;i<=5;i++)
{
    s = s + i;
}
```

Output

```
12345
```

### Problem

Every iteration creates a **new String object** because Strings are immutable.

Memory

```
""

↓

"1"

↓

"12"

↓

"123"

↓

"1234"

↓

"12345"
```

Total Objects

```
6
```

For 100000 iterations

```
100001 Objects
```

This wastes

- Memory
- CPU
- Garbage Collection Time

---

# 3. Solution

Use

```java
StringBuilder sb = new StringBuilder();
```

Now

```java
for(int i=1;i<=5;i++)
{
    sb.append(i);
}
```

Only

```
1 Object
```

is modified repeatedly.

---

# 4. String vs StringBuilder

| Feature | String | StringBuilder |
|----------|---------|---------------|
| Mutable | ❌ | ✅ |
| Object Creation | Every Modification | Same Object |
| Performance | Slow | Fast |
| Memory | High | Low |
| Thread Safe | Yes (Immutable) | No |

---

# 5. Internal Working

Initially

```java
StringBuilder sb = new StringBuilder();
```

Memory

```
Heap

--------------------
_ _ _ _ _ _ _ _ _ _
_ _ _ _ _ _
--------------------

Capacity = 16
```

After

```java
sb.append("Java");
```

```
Heap

--------------------
J A V A _ _ _ _ _ _
_ _ _ _ _ _
--------------------
```

No new object is created.

---

# 6. Creating StringBuilder

## Empty

```java
StringBuilder sb = new StringBuilder();
```

---

## With Initial Value

```java
StringBuilder sb = new StringBuilder("Java");
```

---

## With Capacity

```java
StringBuilder sb = new StringBuilder(50);
```

---

# 7. append()

Adds data at the end.

```java
StringBuilder sb = new StringBuilder();

sb.append("Java");
sb.append(" ");
sb.append("DSA");

System.out.println(sb);
```

Output

```
Java DSA
```

### Complexity

```
O(1) Amortized
```

---

# 8. insert()

Adds data at a specific index.

```java
StringBuilder sb = new StringBuilder("Jva");

sb.insert(1,"a");

System.out.println(sb);
```

Output

```
Java
```

Complexity

```
O(n)
```

---

# 9. delete()

Deletes a range.

```java
StringBuilder sb = new StringBuilder("Java Programming");

sb.delete(4,16);

System.out.println(sb);
```

Output

```
Java
```

Rule

```
[start,end)

Start Included

End Excluded
```

Complexity

```
O(n)
```

---

# 10. deleteCharAt()

Deletes one character.

```java
StringBuilder sb = new StringBuilder("Jxava");

sb.deleteCharAt(1);

System.out.println(sb);
```

Output

```
Java
```

Complexity

```
O(n)
```

---

# 11. replace()

```java
StringBuilder sb = new StringBuilder("I Love C++");

sb.replace(7,10,"Java");

System.out.println(sb);
```

Output

```
I Love Java
```

Complexity

```
O(n)
```

---

# 12. reverse()

```java
StringBuilder sb = new StringBuilder("Nishant");

sb.reverse();

System.out.println(sb);
```

Output

```
tnahsiN
```

Complexity

```
O(n)
```

---

# 13. setCharAt()

```java
StringBuilder sb = new StringBuilder("Java");

sb.setCharAt(1,'o');

System.out.println(sb);
```

Output

```
Jova
```

Complexity

```
O(1)
```

---

# 14. charAt()

```java
char ch = sb.charAt(2);
```

Returns

```
v
```

Complexity

```
O(1)
```

---

# 15. length()

Returns current number of characters.

```java
System.out.println(sb.length());
```

Complexity

```
O(1)
```

---

# 16. capacity()

Returns total storage available before resizing.

```java
StringBuilder sb = new StringBuilder();

System.out.println(sb.capacity());
```

Output

```
16
```

---

Example

```java
StringBuilder sb = new StringBuilder("Java");
```

Length

```
4
```

Capacity

```
20
```

Reason

```
16 + Length
```

---

# 17. ensureCapacity()

Allocates memory in advance.

```java
sb.ensureCapacity(1000);
```

Useful for

- Large Input
- Better Performance

---

# 18. trimToSize()

Reduces unused memory.

```java
sb.trimToSize();
```

Example

Capacity

```
100
```

Length

```
10
```

After

```
Capacity = 10
```

---

# 19. toString()

Converts StringBuilder to String.

```java
StringBuilder sb = new StringBuilder("Java");

String s = sb.toString();
```

---

# 20. Capacity Expansion

Default

```
16
```

Expansion Formula

```
(New Capacity)

=

(Old Capacity × 2)

+

2
```

Example

```
16

↓

34

↓

70

↓

142

↓

286
```

---

# 21. Time Complexity

| Method | Complexity |
|----------|------------|
| append() | O(1) Amortized |
| insert() | O(n) |
| delete() | O(n) |
| deleteCharAt() | O(n) |
| replace() | O(n) |
| reverse() | O(n) |
| charAt() | O(1) |
| setCharAt() | O(1) |
| length() | O(1) |
| capacity() | O(1) |
| toString() | O(n) |

---

# 22. Common Mistakes

## Wrong

```java
StringBuilder sb = "Java";
```

Correct

```java
StringBuilder sb = new StringBuilder("Java");
```

---

Wrong

```java
String s = sb;
```

Correct

```java
String s = sb.toString();
```

---

Wrong

```java
sb.charAt(100);
```

Throws

```
StringIndexOutOfBoundsException
```

---

# 23. Interview Questions

### Q1

Why is StringBuilder faster than String?

Answer

- Mutable
- Same Object Modified
- Less Garbage Collection

---

### Q2

Difference between

```
length()

capacity()
```

---

### Q3

Default Capacity?

```
16
```

---

### Q4

Expansion Formula?

```
(old × 2)+2
```

---

### Q5

Difference

```
StringBuilder

vs

StringBuffer
```

---

### Q6

Can StringBuilder be converted to String?

```
Yes

↓

toString()
```

---

# 24. Cheat Sheet

```
append()          → Add at End

insert()          → Insert at Index

delete()          → Delete Range

deleteCharAt()    → Delete One Character

replace()         → Replace Characters

reverse()         → Reverse String

charAt()          → Get Character

setCharAt()       → Modify Character

length()          → Number of Characters

capacity()        → Total Capacity

ensureCapacity()  → Increase Capacity

trimToSize()      → Remove Extra Capacity

toString()        → Convert to String
```

---

# 25. Practice Questions

## Easy

- Reverse String
- Reverse Words
- Remove Spaces
- Toggle Case
- Remove Digits

---

## Medium

- String Compression
- Reverse Vowels
- Valid Palindrome
- Backspace Compare

---

# 🎯 Revision Summary

✔ Mutable

✔ Fast

✔ Same Object Modified

✔ Default Capacity = 16

✔ Expansion Formula = (Old × 2) + 2

✔ append() → O(1)

✔ reverse() → O(n)

✔ StringBuilder is NOT Thread Safe.



# 📘 05_StringBuffer.md

> **Topic:** Java StringBuffer  
> **Level:** Beginner → Interview Ready  
> **Author:** Nishant Mehra DSA Notes

---

# 📑 Table of Contents

1. What is StringBuffer?
2. Why StringBuffer?
3. Creating StringBuffer
4. Methods
5. StringBuffer vs StringBuilder
6. Synchronization
7. Thread Safety
8. Internal Working
9. Time Complexity
10. Common Mistakes
11. Interview Questions
12. Cheat Sheet
13. Practice Questions

---

# 1. What is StringBuffer?

`StringBuffer` is a **mutable sequence of characters**, just like `StringBuilder`.

The major difference is:

> **StringBuffer is Thread Safe because its methods are synchronized.**

---

# 2. Why StringBuffer?

Suppose two threads are modifying the same object.

```java
Thread A
↓

append("Java")
```

```java
Thread B
↓

delete(0,2)
```

If both execute at the same time,

```
Data Corruption
```

may happen.

To prevent this,

Java introduced

```
StringBuffer
```

---

# 3. Creating StringBuffer

## Empty

```java
StringBuffer sb = new StringBuffer();
```

---

## With String

```java
StringBuffer sb = new StringBuffer("Java");
```

---

## With Capacity

```java
StringBuffer sb = new StringBuffer(50);
```

---

# 4. Methods

Almost all methods are the same as `StringBuilder`.

## append()

```java
StringBuffer sb = new StringBuffer();

sb.append("Java");

sb.append(" DSA");

System.out.println(sb);
```

Output

```
Java DSA
```

---

## insert()

```java
StringBuffer sb = new StringBuffer("Jva");

sb.insert(1,"a");

System.out.println(sb);
```

Output

```
Java
```

---

## delete()

```java
StringBuffer sb = new StringBuffer("Java Programming");

sb.delete(4,16);

System.out.println(sb);
```

Output

```
Java
```

---

## deleteCharAt()

```java
StringBuffer sb = new StringBuffer("Jxava");

sb.deleteCharAt(1);

System.out.println(sb);
```

Output

```
Java
```

---

## replace()

```java
StringBuffer sb = new StringBuffer("I Love C++");

sb.replace(7,10,"Java");

System.out.println(sb);
```

Output

```
I Love Java
```

---

## reverse()

```java
StringBuffer sb = new StringBuffer("Nishant");

sb.reverse();

System.out.println(sb);
```

Output

```
tnahsiN
```

---

## charAt()

```java
char ch = sb.charAt(2);
```

Output

```
v
```

---

## setCharAt()

```java
sb.setCharAt(1,'o');
```

---

## length()

```java
System.out.println(sb.length());
```

---

## capacity()

```java
System.out.println(sb.capacity());
```

Default

```
16
```

---

## ensureCapacity()

```java
sb.ensureCapacity(1000);
```

---

## trimToSize()

```java
sb.trimToSize();
```

---

## toString()

```java
String s = sb.toString();
```

---

# 5. StringBuilder vs StringBuffer

| Feature | StringBuilder | StringBuffer |
|----------|---------------|--------------|
| Mutable | ✅ | ✅ |
| Thread Safe | ❌ | ✅ |
| Synchronization | ❌ | ✅ |
| Performance | Faster | Slightly Slower |
| Multi-threading | ❌ | ✅ |
| Introduced | Java 5 | Java 1.0 |

---

# 6. Synchronization

Every important method in `StringBuffer` is synchronized.

Example (conceptually)

```java
public synchronized StringBuffer append(String str)
{
    ...
}
```

Only one thread can execute a synchronized method at a time.

This prevents race conditions.

---

# 7. Thread Safety

## StringBuilder

```
Thread A
↓

append()
```

```
Thread B
↓

delete()
```

Both can execute together.

Result

```
❌ Data may become inconsistent.
```

---

## StringBuffer

```
Thread A

↓

LOCK

↓

append()

↓

UNLOCK
```

Only after Thread A finishes can Thread B enter.

Result

```
✅ Safe
```

---

# 8. Internal Working

`StringBuffer` also stores characters in a resizable array.

Example

```java
StringBuffer sb = new StringBuffer("Java");
```

Memory

```
Heap

--------------------
J A V A _ _ _ _ _ _
_ _ _ _ _ _
--------------------
```

Like `StringBuilder`, it grows automatically when capacity is exceeded.

---

# 9. Time Complexity

| Method | Complexity |
|----------|------------|
| append() | O(1) Amortized |
| insert() | O(n) |
| delete() | O(n) |
| deleteCharAt() | O(n) |
| replace() | O(n) |
| reverse() | O(n) |
| charAt() | O(1) |
| setCharAt() | O(1) |
| length() | O(1) |
| capacity() | O(1) |
| toString() | O(n) |

> Note: In practice, `StringBuffer` is slightly slower than `StringBuilder` because of synchronization overhead.

---

# 10. Common Mistakes

## ❌ Wrong

```java
StringBuffer sb = "Java";
```

✅ Correct

```java
StringBuffer sb = new StringBuffer("Java");
```

---

## ❌ Wrong

```java
String s = sb;
```

✅ Correct

```java
String s = sb.toString();
```

---

## ❌ Wrong

```java
sb.charAt(100);
```

Throws

```
StringIndexOutOfBoundsException
```

---

# 11. Interview Questions

### Q1. Difference between StringBuilder and StringBuffer?

**Answer:**

- Both are mutable.
- `StringBuilder` is faster.
- `StringBuffer` is synchronized and thread-safe.

---

### Q2. Which one should you use?

**Single-threaded application**

```
StringBuilder
```

**Multi-threaded application**

```
StringBuffer
```

---

### Q3. Why is StringBuffer slower?

Because every important method is synchronized.

---

### Q4. Is StringBuffer immutable?

```
No.
```

It is mutable.

---

### Q5. Can StringBuffer be converted to String?

```java
String s = sb.toString();
```

Yes.

---

# 12. Cheat Sheet

```
String            → Immutable

StringBuilder     → Mutable + Fast

StringBuffer      → Mutable + Thread Safe
```

---

```
append()          → Add at End

insert()          → Insert

delete()          → Delete Range

deleteCharAt()    → Delete One Character

replace()         → Replace

reverse()         → Reverse

charAt()          → Get Character

setCharAt()       → Modify Character

length()          → Characters

capacity()        → Storage Capacity

toString()        → Convert to String
```

---

# 13. When to Use What?

| Situation | Best Choice |
|-----------|-------------|
| Fixed text | String |
| Frequent modifications | StringBuilder |
| Multi-threaded modifications | StringBuffer |

---

# 14. Practice Questions

## Theory

1. What is synchronization?
2. Why is StringBuffer thread-safe?
3. Difference between StringBuilder and StringBuffer?
4. Why is StringBuilder faster?

---

## Coding

### Q1

Create

```java
StringBuffer sb = new StringBuffer("Java");
```

Append

```
 Programming
```

Output

```
Java Programming
```

---

### Q2

Reverse

```
Nishant
```

using `reverse()`.

---

### Q3

Replace

```
Python
```

with

```
Java
```

in

```
I Love Python
```

---

### Q4

Delete the character `'x'` from

```
Jxava
```

---

# 🎯 Revision Summary

✔ StringBuffer is mutable.

✔ It is thread-safe.

✔ Methods are synchronized.

✔ Slightly slower than StringBuilder.

✔ Use StringBuilder in most coding interviews unless thread safety is required.

---

# 📌 Final Comparison

| Feature | String | StringBuilder | StringBuffer |
|--------|--------|---------------|--------------|
| Mutable | ❌ | ✅ | ✅ |
| Thread Safe | ✅ (Immutable) | ❌ | ✅ |
| Fast | ❌ | ✅ | ⚠️ Slightly Slower |
| Memory Efficient for Modifications | ❌ | ✅ | ✅ |
| Best Use Case | Constant text | Single-threaded modifications | Multi-threaded modifications |

---

> ⭐ End of `05_StringBuffer.md`




---

> ⭐ End of `04_StringBuilder.md`
