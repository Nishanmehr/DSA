
# 📘 Java Strings - Part 1 (String Basics)

> 📚 Language: Java
> 🎯 Level: Beginner → Intermediate
> 👨‍💻 Author: Nishant Mehra DSA Notes

---

# 📑 Table of Contents

1. What is String?
2. Why do we need String?
3. String as an Object
4. Ways to Create String
5. Memory Management
6. Stack vs Heap
7. String Constant Pool (SCP)
8. String Literal
9. `new String()`
10. Memory Examples
11. `==` vs `equals()`
12. Immutability
13. Interview Questions
14. Common Mistakes
15. Complexity
16. Revision Summary

---

# 1️⃣ What is String?

A **String** is a sequence of characters enclosed inside double quotes (`"`).

Example:

```java
String name = "Nishant";
```

Internally,

```
N i s h a n t
```

Each character has an index.

```
Character : N  i  s  h  a  n  t
Index     : 0  1  2  3  4  5  6
```

---

# 2️⃣ Why do we need String?

Without String,

```
'N'
'i'
's'
'h'
'a'
'n'
't'
```

Every character must be stored separately.

With String,

```java
String name = "Nishant";
```

All characters are stored together.

---

# 3️⃣ String is a Class

Many beginners think String is a primitive datatype.

❌ Wrong.

String is a predefined class inside `java.lang` package.

```java
String name = "Java";
```

is internally equivalent to

```java
String name = new String("Java");
```

except for memory optimization using the String Pool.

---

# 4️⃣ Ways to Create String

## Method 1 : String Literal

```java
String s = "Java";
```

Uses

- String Constant Pool

---

## Method 2 : Using new Keyword

```java
String s = new String("Java");
```

Uses

- String Constant Pool
- Heap Memory

---

# 5️⃣ Memory Management

Java Memory is mainly divided into:

```
JVM
│
├── Stack Memory
│
└── Heap Memory
```

---

## Stack Memory

Stores

- Local Variables
- References
- Method Calls

Example

```java
String s = "Java";
```

Stack

```
s
```

Only the reference is stored here.

---

## Heap Memory

Stores

- Objects
- Arrays
- Collections
- Strings

Actual String objects are stored in Heap.

---

# 6️⃣ String Constant Pool (SCP)

The String Constant Pool is a special memory area inside Heap.

Purpose

- Avoid duplicate String objects.
- Save memory.
- Improve performance.

Example

```java
String s1 = "Java";
String s2 = "Java";
```

Memory

```
STACK

s1 --------\
             \
              -----> "Java"
             /
s2 --------/


STRING POOL

"Java"
```

Total Objects

```
1
```

Both variables point to the same object.

---

# 7️⃣ String Literal

```java
String city = "Delhi";
```

Execution

Step 1

Java checks the String Pool.

```
Already Present?

YES

↓

Reuse Object

NO

↓

Create Object
```

---

Example

```java
String a = "Hello";
String b = "Hello";
```

Objects Created

```
1
```

References

```
2
```

---

# 8️⃣ new String()

Example

```java
String s = new String("Java");
```

Execution

### Step 1

Java checks the String Pool.

Pool

```
Java
```

If absent, it creates it.

---

### Step 2

`new` keyword forces Java to create another object in Heap.

Memory

```
STACK

s

↓

HEAP

Java

↓

STRING POOL

Java
```

Total Objects

```
2
```

---

Example

```java
String s1 = new String("Java");
String s2 = new String("Java");
```

Memory

```
STACK

s1 ---> Heap Object 1

s2 ---> Heap Object 2


STRING POOL

Java
```

Total Objects

```
3
```

---

# 9️⃣ Memory Examples

## Example 1

```java
String s1 = "ABC";
String s2 = "ABC";
```

Objects

```
1
```

---

## Example 2

```java
String s1 = new String("ABC");
String s2 = new String("ABC");
```

Objects

```
Pool : 1

Heap : 2

Total : 3
```

---

## Example 3

```java
String s1 = "ABC";
String s2 = new String("ABC");
```

Objects

```
Pool : 1

Heap : 1

Total : 2
```

---

# 🔟 == vs equals()

## ==

Compares

```
Reference (Memory Address)
```

Example

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

Output

```
true
```

Because both references point to the same object.

---

Example

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output

```
false
```

Different Heap objects.

---

## equals()

Compares

```
Actual Content
```

Example

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1.equals(s2));
```

Output

```
true
```

---

## Summary

| Operator | Compares |
|----------|----------|
| `==` | Reference |
| `equals()` | Content |

---

# 1️⃣1️⃣ Immutability

## Definition

A String object cannot be modified after it is created.

Example

```java
String s = "Hello";

s = "World";
```

Did

```
Hello

↓

World
```

happen?

❌ No.

Memory

```
Before

s

↓

Hello
```

After

```
s

↓

World


Hello
```

A new object is created.

The old object remains unchanged.

---

## Why is String Immutable?

### 1. Security

Database URLs

Passwords

File Paths

cannot be modified accidentally.

---

### 2. String Pool

Multiple variables safely share one object.

---

### 3. Thread Safety

Multiple threads can use the same String without synchronization.

---

### 4. HashMap Keys

String hash codes remain stable.

---

### 5. Performance

Objects can be reused from the String Pool.

---

# 🧠 Interview Questions

### Q1

Difference between

```java
==
```

and

```java
equals()
```

---

### Q2

How many objects are created?

```java
String s1 = "Java";
String s2 = new String("Java");
```

Answer

```
2
```

---

### Q3

Why are Strings immutable?

Expected Answer

- Security
- String Pool
- Thread Safety
- HashMap
- Performance

---

### Q4

Where is String Constant Pool located?

Answer

```
Inside Heap Memory
```

---

### Q5

Does

```java
s = "World";
```

modify the existing String?

```
No
```

It changes the reference.

---

# ⚠ Common Mistakes

### ❌ Wrong

```java
if(username == "admin")
```

### ✅ Correct

```java
if(username.equals("admin"))
```

---

### ❌ Wrong

```java
String s = "Java";

s.replace("Java","Python");

System.out.println(s);
```

Output

```
Java
```

---

### ✅ Correct

```java
s = s.replace("Java","Python");
```

---

# ⏱ Time Complexity

| Operation | Complexity |
|-----------|-----------|
| String Literal Lookup | O(1) |
| `==` | O(1) |
| `equals()` | O(n) |
| Object Creation | O(n) |

---

# 📝 Revision Summary

- ✅ String is a class.
- ✅ String objects are stored in Heap.
- ✅ String Literals use the String Constant Pool.
- ✅ `new String()` creates a new Heap object.
- ✅ `==` compares references.
- ✅ `equals()` compares contents.
- ✅ Strings are immutable.
- ✅ String Pool improves memory usage.
- ✅ Variables can change references, but String objects never change.

---

# 🎯 Practice Questions

1. How many objects are created?

```java
String a = "Java";
String b = "Java";
String c = new String("Java");
```

2. Explain String Pool with a diagram.

3. Why are Strings immutable?

4. Difference between Heap and Stack.

5. Explain `==` vs `equals()` with examples.

---


# 📘 Java Strings - Part 2 (String Methods)

> 📚 Language: Java
> 🎯 Level: Beginner → Intermediate
> 👨‍💻 Author: Nishant Mehra DSA Notes

---

# 📑 Table of Contents

1. length()
2. charAt()
3. substring()
4. indexOf()
5. lastIndexOf()
6. contains()
7. startsWith()
8. endsWith()
9. equals()
10. equalsIgnoreCase()
11. compareTo()
12. toUpperCase()
13. toLowerCase()
14. trim()
15. isEmpty()
16. isBlank()
17. concat()
18. replace()
19. replaceFirst()
20. replaceAll()
21. split()
22. repeat()
23. matches()

---

# 1️⃣ length()

Returns the total number of characters.

### Syntax

```java
str.length();
```

### Return Type

```java
int
```

### Example

```java
String s = "Nishant";
System.out.println(s.length());
```

Output

```
7
```

### Complexity

```
O(1)
```

> 💡 Remember: `String.length()` is a method, but `array.length` is a property.

---

# 2️⃣ charAt()

Returns the character at a given index.

### Syntax

```java
str.charAt(index);
```

### Return Type

```java
char
```

### Example

```java
String s = "Nishant";

System.out.println(s.charAt(0));
```

Output

```
N
```

---

### Example

```java
System.out.println(s.charAt(4));
```

Output

```
a
```

---

### Exception

```java
s.charAt(100);
```

Throws

```
StringIndexOutOfBoundsException
```

### Complexity

```
O(1)
```

---

# 3️⃣ substring()

Extracts a part of the String.

## Syntax 1

```java
str.substring(beginIndex);
```

Returns

```
beginIndex → end
```

Example

```java
String s="Programming";

System.out.println(s.substring(3));
```

Output

```
gramming
```

---

## Syntax 2

```java
str.substring(beginIndex,endIndex);
```

Rule

```
[beginIndex, endIndex)
```

Left Included ✅

Right Excluded ❌

Example

```java
String s="Programming";

System.out.println(s.substring(3,7));
```

Output

```
gram
```

### Complexity

```
O(n)
```

---

# 4️⃣ indexOf()

Returns the first occurrence of a character or substring.

### Syntax

```java
str.indexOf('a');
```

or

```java
str.indexOf("Java");
```

### Example

```java
String s="Programming";

System.out.println(s.indexOf('g'));
```

Output

```
3
```

---

If not found

```
-1
```

### Complexity

```
O(n)
```

---

# 5️⃣ lastIndexOf()

Returns the last occurrence.

Example

```java
String s="Programming";

System.out.println(s.lastIndexOf('m'));
```

Output

```
7
```

### Complexity

```
O(n)
```

---

# 6️⃣ contains()

Checks whether a substring exists.

### Syntax

```java
str.contains("Java");
```

### Return Type

```java
boolean
```

### Example

```java
String s="Programming";

System.out.println(s.contains("gram"));
```

Output

```
true
```

---

# 7️⃣ startsWith()

Checks prefix.

Example

```java
String s="Programming";

System.out.println(s.startsWith("Pro"));
```

Output

```
true
```

---

# 8️⃣ endsWith()

Checks suffix.

Example

```java
String s="Programming";

System.out.println(s.endsWith("ing"));
```

Output

```
true
```

---

# 9️⃣ equals()

Compares content.

### Example

```java
String s1="Java";
String s2="Java";

System.out.println(s1.equals(s2));
```

Output

```
true
```

### Complexity

```
O(n)
```

---

# 🔟 equalsIgnoreCase()

Ignores letter case.

Example

```java
String s1="Java";
String s2="JAVA";

System.out.println(s1.equalsIgnoreCase(s2));
```

Output

```
true
```

---

# 1️⃣1️⃣ compareTo()

Lexicographical comparison.

### Syntax

```java
str1.compareTo(str2);
```

### Returns

| Value | Meaning |
|------|---------|
| < 0 | First comes before second |
| = 0 | Equal |
| > 0 | First comes after second |

Example

```java
"Apple".compareTo("Ball")
```

Output

```
Negative
```

Example

```java
"Dog".compareTo("Cat")
```

Output

```
Positive
```

---

# 1️⃣2️⃣ toUpperCase()

Converts to uppercase.

```java
String s="java";

System.out.println(s.toUpperCase());
```

Output

```
JAVA
```

---

# 1️⃣3️⃣ toLowerCase()

Converts to lowercase.

```java
String s="JAVA";

System.out.println(s.toLowerCase());
```

Output

```
java
```

---

# 1️⃣4️⃣ trim()

Removes leading and trailing spaces.

```java
String s="   Java   ";

System.out.println(s.trim());
```

Output

```
Java
```

> ⚠️ `trim()` does **not** remove spaces in the middle.

---

# 1️⃣5️⃣ isEmpty()

Checks whether length is 0.

```java
"".isEmpty()
```

Output

```
true
```

```java
" ".isEmpty()
```

Output

```
false
```

---

# 1️⃣6️⃣ isBlank()

Java 11+

Checks whether a string is empty or contains only whitespace.

```java
"   ".isBlank()
```

Output

```
true
```

Difference:

| String | isEmpty() | isBlank() |
|--------|-----------|-----------|
| `""` | ✅ | ✅ |
| `" "` | ❌ | ✅ |
| `"Java"` | ❌ | ❌ |

---

# 1️⃣7️⃣ concat()

Joins strings.

```java
String first="Nishant";
String last="Mehra";

System.out.println(first.concat(" ").concat(last));
```

Output

```
Nishant Mehra
```

---

# 1️⃣8️⃣ replace()

Replaces all literal occurrences.

```java
String s="banana";

System.out.println(s.replace('a','o'));
```

Output

```
bonono
```

Example

```java
String s="I love Java";

System.out.println(s.replace("Java","Python"));
```

Output

```
I love Python
```

> ⚠️ Strings are immutable. Assign the result back if you want the change to persist.

---

# 1️⃣9️⃣ replaceFirst()

Replaces only the first occurrence.

```java
String s="one one one";

System.out.println(s.replaceFirst("one","two"));
```

Output

```
two one one
```

---

# 2️⃣0️⃣ replaceAll()

Replaces all matches using **regular expressions**.

```java
String s="one one one";

System.out.println(s.replaceAll("one","two"));
```

Output

```
two two two
```

> 💡 Difference:
> - `replace()` → Literal replacement
> - `replaceAll()` → Regex replacement

---

# 2️⃣1️⃣ split()

Splits a string into an array.

```java
String s="Java,Python,C++";

String[] arr=s.split(",");
```

Output

```
Java
Python
C++
```

Count words

```java
String s="I love Java";

System.out.println(s.split(" ").length);
```

Output

```
3
```

---

# 2️⃣2️⃣ repeat()

Java 11+

```java
System.out.println("Hi".repeat(3));
```

Output

```
HiHiHi
```

---

# 2️⃣3️⃣ matches()

Checks whether a string matches a regular expression.

```java
String s="12345";

System.out.println(s.matches("\\d+"));
```

Output

```
true
```

---

# 📊 Complexity Table

| Method | Complexity |
|---------|------------|
| length() | O(1) |
| charAt() | O(1) |
| substring() | O(n) |
| indexOf() | O(n) |
| lastIndexOf() | O(n) |
| contains() | O(n) |
| startsWith() | O(k) |
| endsWith() | O(k) |
| equals() | O(n) |
| compareTo() | O(n) |
| trim() | O(n) |
| replace() | O(n) |
| split() | O(n) |
| repeat() | O(n × count) |

---

# ⚠️ Common Mistakes

### ❌ Using `==` instead of `equals()`

```java
if(name == "Java")
```

### ✅ Correct

```java
if(name.equals("Java"))
```

---

### ❌ Forgetting immutability

```java
String s = "Java";
s.replace("Java","Python");

System.out.println(s);
```

Output

```
Java
```

Correct

```java
s = s.replace("Java","Python");
```

---

# 📝 Revision Summary

- `length()` → Count characters
- `charAt()` → Character at index
- `substring()` → Extract part
- `indexOf()` → First occurrence
- `lastIndexOf()` → Last occurrence
- `contains()` → Search substring
- `startsWith()` / `endsWith()` → Prefix/Suffix check
- `equals()` → Compare content
- `compareTo()` → Lexicographical order
- `trim()` → Remove leading/trailing spaces
- `replace()` → Literal replacement
- `split()` → Convert String → Array
- `repeat()` → Repeat text
- `matches()` → Regex matching

---

# 🎯 Practice Questions

1. Print the first and last character of a String.
2. Extract `"gram"` from `"Programming"`.
3. Count the number of words in `"Java is awesome"`.
4. Replace all spaces with `-`.
5. Check whether a string starts with `"Mr."`.
6. Compare two strings ignoring case.
7. Reverse a string using `substring()` (logic practice).

---

> ⭐ End of Part 2
> Next File: **03_Character_Class.md**


# 📘 Java Strings - Part 3 (Character Class)

> 📚 Language: Java
> 🎯 Level: Beginner → Intermediate
> 👨‍💻 Author: Nishant Mehra DSA Notes

---

# 📑 Table of Contents

1. What is Character Class?
2. Primitive vs Wrapper
3. ASCII Table
4. Unicode
5. Character Methods
6. Common DSA Patterns
7. Coding Questions
8. Interview Questions
9. Complexity
10. Revision Summary

---

# 1️⃣ What is Character Class?

Java provides a wrapper class named **Character** to perform operations on characters.

Without Character class,

Suppose we have

```java
char ch = 'A';
```

How do we know?

- Is it a letter?
- Is it a digit?
- Is it uppercase?
- Is it lowercase?
- Is it whitespace?

This is where the `Character` class helps.

---

# 2️⃣ Primitive vs Wrapper

| Primitive | Wrapper |
|------------|----------|
| int | Integer |
| char | Character |
| double | Double |
| float | Float |
| boolean | Boolean |

Wrapper classes provide useful methods.

Example

```java
Character.isDigit(ch);
```

---

# 3️⃣ ASCII Table

Every character has a numeric ASCII value.

| Character | ASCII |
|-----------|------:|
| A | 65 |
| B | 66 |
| C | 67 |
| Z | 90 |
| a | 97 |
| b | 98 |
| c | 99 |
| z | 122 |
| 0 | 48 |
| 1 | 49 |
| 9 | 57 |
| Space | 32 |

---

## Character to ASCII

```java
char ch='A';

System.out.println((int)ch);
```

Output

```
65
```

---

## ASCII to Character

```java
int x=97;

System.out.println((char)x);
```

Output

```
a
```

---

# 4️⃣ Unicode

ASCII supports only 128 characters.

Java uses **Unicode**, so it supports almost every language.

Examples

- English
- Hindi
- Japanese
- Chinese
- Emoji

Example

```java
char ch='अ';
```

Valid in Java.

---

# 5️⃣ Character Methods

---

## isLetter()

Checks whether a character is an alphabet.

```java
Character.isLetter('A');
```

Output

```
true
```

```java
Character.isLetter('9');
```

Output

```
false
```

---

## isDigit()

Checks whether a character is a digit.

```java
Character.isDigit('8');
```

Output

```
true
```

```java
Character.isDigit('A');
```

Output

```
false
```

---

## isLetterOrDigit()

Checks whether a character is either a letter or digit.

```java
Character.isLetterOrDigit('A');
```

Output

```
true
```

```java
Character.isLetterOrDigit('7');
```

Output

```
true
```

```java
Character.isLetterOrDigit('#');
```

Output

```
false
```

---

## isUpperCase()

```java
Character.isUpperCase('A');
```

Output

```
true
```

```java
Character.isUpperCase('a');
```

Output

```
false
```

---

## isLowerCase()

```java
Character.isLowerCase('z');
```

Output

```
true
```

---

## toUpperCase()

```java
Character.toUpperCase('m');
```

Output

```
M
```

---

## toLowerCase()

```java
Character.toLowerCase('K');
```

Output

```
k
```

---

## isWhitespace()

Checks for

- Space
- Tab
- New Line

```java
Character.isWhitespace(' ');
```

Output

```
true
```

---

## getNumericValue()

Converts numeric character into integer.

```java
Character.getNumericValue('8');
```

Output

```
8
```

---

# 6️⃣ Common DSA Patterns

## Count Letters

```java
int count=0;

for(int i=0;i<s.length();i++)
{
    if(Character.isLetter(s.charAt(i)))
        count++;
}
```

---

## Count Digits

```java
int count=0;

for(int i=0;i<s.length();i++)
{
    if(Character.isDigit(s.charAt(i)))
        count++;
}
```

---

## Count Uppercase

```java
int count=0;

for(int i=0;i<s.length();i++)
{
    if(Character.isUpperCase(s.charAt(i)))
        count++;
}
```

---

## Count Lowercase

```java
int count=0;

for(int i=0;i<s.length();i++)
{
    if(Character.isLowerCase(s.charAt(i)))
        count++;
}
```

---

## Count Special Characters

```java
int count=0;

for(int i=0;i<s.length();i++)
{
    char ch=s.charAt(i);

    if(!Character.isLetterOrDigit(ch))
        count++;
}
```

---

## Toggle Case

```java
for(int i=0;i<s.length();i++)
{
    char ch=s.charAt(i);

    if(Character.isUpperCase(ch))
        System.out.print(Character.toLowerCase(ch));
    else
        System.out.print(Character.toUpperCase(ch));
}
```

Input

```
JaVa
```

Output

```
jAvA
```

---

## Remove Digits

```java
StringBuilder ans=new StringBuilder();

for(int i=0;i<s.length();i++)
{
    char ch=s.charAt(i);

    if(!Character.isDigit(ch))
        ans.append(ch);
}
```

---

# 7️⃣ Coding Questions

## Q1 Count Letters

Input

```
abc123XYZ
```

Output

```
Letters = 6
```

---

## Q2 Count Digits

Input

```
abc123
```

Output

```
3
```

---

## Q3 Count Uppercase

Input

```
JavaDSA
```

Output

```
4
```

---

## Q4 Toggle Case

Input

```
Hello
```

Output

```
hELLO
```

---

## Q5 Remove Digits

Input

```
abc123xyz
```

Output

```
abcxyz
```

---

## Q6 Count Special Characters

Input

```
abc123@#$
```

Output

```
3
```

---

# 8️⃣ Interview Questions

## Difference

```java
Character.isDigit(ch)
```

vs

```java
Character.getNumericValue(ch)
```

### Answer

`isDigit()`

- Checks whether the character is a digit.
- Returns boolean.

`getNumericValue()`

- Converts numeric character to integer.
- Returns int.

---

## Which is better?

```java
ch-'0'
```

or

```java
Character.getNumericValue(ch)
```

### Answer

For DSA,

```java
ch-'0'
```

is faster and commonly used for `'0'`–`'9'`.

---

# 9️⃣ Complexity

All Character methods

```
O(1)
```

because they work on a single character.

---

# 🔟 Common Mistakes

❌ Wrong

```java
if(ch>='0' && ch<='9')
```

This works, but is less readable.

✅ Better

```java
Character.isDigit(ch)
```

---

❌ Wrong

```java
if(ch>='A' && ch<='Z')
```

✅ Better

```java
Character.isUpperCase(ch)
```

---

# 📝 Revision Summary

✔ Character is a Wrapper Class.

✔ ASCII assigns numeric values to characters.

✔ Java internally supports Unicode.

✔ Most Used Methods

- isLetter()
- isDigit()
- isLetterOrDigit()
- isUpperCase()
- isLowerCase()
- toUpperCase()
- toLowerCase()
- isWhitespace()
- getNumericValue()

✔ Character methods are heavily used in

- Valid Palindrome
- Valid Anagram
- Password Validation
- Remove Special Characters
- Count Digits
- Count Letters
- Toggle Case
- String Parsing

---

# 🎯 Practice Set

1. Count vowels.
2. Count consonants.
3. Count digits.
4. Count spaces.
5. Count special characters.
6. Toggle case.
7. Remove digits.
8. Remove special characters.
9. Print only uppercase letters.
10. Print only lowercase letters.

---

# 🚀 LeetCode Problems

### Easy

- LC 125 - Valid Palindrome
- LC 709 - To Lower Case
- LC 520 - Detect Capital
- LC 917 - Reverse Only Letters

### Medium

- LC 151 - Reverse Words in a String
- LC 8 - String to Integer (atoi)

---

> ⭐ End of Part 3
> Next File: **04_String_CheatSheet.md**

# 📘 Java Strings - Part 4 (Interview Cheat Sheet)

> 📚 Language: Java
> 🎯 Revision Notes
> ⏱ Read Time: 15 Minutes

---

# 🔥 String Revision Mind Map

```

```
                        String
                           │
        ┌──────────────────┴──────────────────┐
        │                                     │
   String Memory                       String Methods
        │                                     │
   ├── Heap                           ├── length()
   ├── Stack                          ├── charAt()
   ├── SCP                            ├── substring()
   └── Immutable                      ├── indexOf()
                                      ├── replace()
                                      ├── split()
                                      ├── equals()
                                      └── compareTo()

```

---

# 📌 String Memory

```
String s="Java";
```

Memory

```
Stack

s

↓

String Pool

Java
```

---

```
String s=new String("Java");
```

Memory

```
Stack

↓

Heap Object

↓

String Pool
```

Objects

```
2
```

---

# 📌 String Pool

Purpose

✔ Save Memory

✔ Avoid Duplicate Objects

✔ Faster Comparison

---

# 📌 == vs equals()

| == | equals() |
|----|-----------|
| Compare Reference | Compare Content |
| O(1) | O(n) |
| Memory Address | Actual Value |

---

Example

```java
String a="Java";
String b="Java";

a==b
```

```
true
```

---

```java
String a=new String("Java");
String b=new String("Java");

a==b
```

```
false
```

---

```java
a.equals(b)
```

```
true
```

---

# 📌 Immutability

```
String s="Java";

s="Python";
```

Old object

```
Java
```

still exists.

A new object

```
Python
```

is created.

---

# 📌 Most Used Methods

| Method | Purpose |
|----------|----------|
| length() | Size |
| charAt() | Character |
| substring() | Extract |
| indexOf() | Search |
| contains() | Search |
| replace() | Replace |
| split() | Convert to Array |
| trim() | Remove edge spaces |
| equals() | Compare |
| compareTo() | Lexicographic |

---

# 📌 Character Methods

| Method | Purpose |
|----------|----------|
| isLetter() | Alphabet |
| isDigit() | Digit |
| isUpperCase() | Uppercase |
| isLowerCase() | Lowercase |
| isWhitespace() | Space |
| toUpperCase() | Convert |
| toLowerCase() | Convert |
| getNumericValue() | Character → Integer |

---

# 📌 ASCII Tricks

| Character | ASCII |
|-----------|------:|
| A | 65 |
| Z | 90 |
| a | 97 |
| z | 122 |
| 0 | 48 |
| 9 | 57 |

### Most Important

```
'a' - 'A' = 32
```

Meaning

```
Lowercase

=

Uppercase + 32
```

Convert manually

```java
char upper='A';

char lower=(char)(upper+32);
```

---

# 📌 Complexity Table

| Operation | Complexity |
|------------|------------|
| length() | O(1) |
| charAt() | O(1) |
| equals() | O(n) |
| compareTo() | O(n) |
| contains() | O(n) |
| substring() | O(n) |
| replace() | O(n) |
| split() | O(n) |

---

# 📌 Most Asked Interview Questions

### Q1

Difference

```
==
```

vs

```
equals()
```

---

### Q2

Why is String immutable?

Answer

- Security
- Thread Safety
- HashMap Keys
- String Pool
- Performance

---

### Q3

Where is String Pool?

```
Heap
```

---

### Q4

Difference

```
StringBuilder

vs

StringBuffer
```

Answer

```
Next Topic 🙂
```

---

### Q5

Difference

```
trim()

vs

strip()
```

Answer

```
trim()

↓

ASCII Spaces

strip()

↓

Unicode Spaces
```

---

### Q6

Difference

```
replace()

vs

replaceAll()
```

Answer

```
replace()

↓

Literal

replaceAll()

↓

Regex
```

---

# 📌 Common Exceptions

### 1

```
StringIndexOutOfBoundsException
```

Reason

```
charAt()

substring()
```

Wrong index.

---

### 2

```
NullPointerException
```

Reason

```java
String s=null;

s.length();
```

---

# 📌 Common Mistakes

❌

```java
if(name=="Java")
```

✔

```java
if(name.equals("Java"))
```

---

❌

```java
s.replace("Java","Python");
```

✔

```java
s=s.replace("Java","Python");
```

---

❌

```java
substring(2,5)
```

Thinking

```
2

↓

5
```

Correct

```
2

↓

4
```

Right index excluded.

---

# 📌 DSA Patterns

Almost every String problem belongs to one of these patterns:

1. Traversal
2. Frequency Array
3. Two Pointer
4. Sliding Window
5. HashMap
6. Stack
7. StringBuilder
8. Prefix Matching
9. Character Counting
10. Palindrome

---

# 📌 Beginner Problems

- Reverse String
- Palindrome
- Count Vowels
- Count Consonants
- Count Digits
- Count Spaces
- Count Special Characters
- Toggle Case
- Reverse Words
- Remove Duplicates

---

# 📌 Easy LeetCode

| LC | Problem |
|----|---------|
| 344 | Reverse String |
| 125 | Valid Palindrome |
| 58 | Length of Last Word |
| 28 | Find Index of First Occurrence |
| 14 | Longest Common Prefix |
| 387 | First Unique Character |
| 242 | Valid Anagram |
| 709 | To Lower Case |
| 520 | Detect Capital |

---

# 📌 Medium LeetCode

| LC | Problem |
|----|---------|
| 49 | Group Anagrams |
| 151 | Reverse Words |
| 3 | Longest Substring Without Repeating Characters |
| 5 | Longest Palindromic Substring |
| 438 | Find All Anagrams |
| 8 | String to Integer (atoi) |

---

# 🎯 One-Line Revision

✔ String is immutable.

✔ String is a class.

✔ String Pool avoids duplicate objects.

✔ `==` compares references.

✔ `equals()` compares content.

✔ `charAt()` → Character

✔ `substring()` → Extract

✔ `split()` → Array

✔ `replace()` → Replace

✔ `compareTo()` → Lexicographic

✔ Character class handles letters, digits, uppercase, lowercase, and whitespace.

---
