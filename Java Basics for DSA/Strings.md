
# 📘 Java Strings — Beginner to Theoretical Pro

---

## 🧵 What is a String in Java?
A sequence of characters — like `"Hello"` is 5 characters.

In Java, `String` is an **object**, not a primitive.

Strings are **immutable** → once created, cannot be changed.

```java
String s = "Hello";
s.concat(" World"); 
System.out.println(s); // prints "Hello" (NOT "Hello World")
```

---

## ✍️ How to Create a String

```java
String s1 = "Hello";            // String literal
String s2 = new String("Hi");   // Using constructor
char[] arr = {'J', 'a', 'v', 'a'};
String s3 = new String(arr);    // From char array
```

---

## ⚠️ Important: String Immutability

Any method that modifies a string actually returns a **new object**.

```java
String s = "abc";
s.toUpperCase();        // Doesn't change original
System.out.println(s);  // prints "abc"
s = s.toUpperCase();    // Now s becomes "ABC"
```

---

## 🔧 StringBuilder vs StringBuffer vs String

| Feature      | String | StringBuilder | StringBuffer |
|--------------|--------|---------------|--------------|
| Mutable      | ❌ No  | ✅ Yes        | ✅ Yes       |
| Thread-safe  | ❌ No  | ❌ No         | ✅ Yes       |
| Performance  | ⚠️ Slow | ✅ Fast       | ⚠️ Slower    |
| Use Case     | Fixed string | Heavy editing | Multi-threaded edit |

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // Hello World
```

---

## 🔑 Must-Know String Methods

### 💬 Basic Operations:

```java
s.length();            
s.charAt(i);           
s.equals("hello");     
s.equalsIgnoreCase();  
s.compareTo();         
s.isEmpty();           
```

### 🔍 Searching:

```java
s.indexOf("lo");       
s.lastIndexOf("l");    
s.contains("el");      
s.startsWith("He");    
s.endsWith("lo");      
```

### 🔨 Modifying:

```java
s.toLowerCase();       
s.toUpperCase();
s.trim();              
s.replace("a", "b");   
s.replaceAll(regex, replacement);
```

### 📐 Substring:

```java
s.substring(2);        
s.substring(2, 4);     
```

### 🪓 Splitting & Joining:

```java
String[] parts = s.split(" ");
String joined = String.join("-", "Java", "Rocks"); // Java-Rocks
```

### 🔤 Conversion:

```java
String.valueOf(123);        
Integer.parseInt("456");    
String str = new String(charArray);
```

---

## ✨ StringBuilder Cheat Sheet

```java
StringBuilder sb = new StringBuilder("Hello");

sb.append(" World");          
sb.insert(5, ",");            
sb.delete(5, 6);              
sb.reverse();                 
sb.setCharAt(0, 'h');         
```

---

## 💡 Tips & Tricks

✅ Always use `StringBuilder` for string concatenation inside loops.  
✅ Use `.equals()` for comparing strings, not `==`.  
✅ Prefer `char[]` when modifying characters in-place.  
✅ `trim()` removes only outside spaces — not all whitespaces inside.  
✅ Use `split(" ")` carefully — multiple spaces cause empty strings.  
✅ Use `replaceAll("\s+", " ")` to normalize spaces.  

**Reverse words example:**

```java
String[] words = s.split(" ");
Collections.reverse(Arrays.asList(words));
String reversed = String.join(" ", words);
```

---

## ❌ Common Mistakes to Avoid

- `s == "hello"` → wrong for value check, use `s.equals("hello")`
- Forgetting `s = s.toUpperCase()` — string methods return new objects
- Using `String` in loops with `+=` → leads to performance issues
- Mixing `char` and `String` in comparison
- `split("")` gives all characters, not words
- `substring(i, j)` → excludes `j`

---

## 📦 Real-world Example: Capitalize First Letter of Each Word

```java
String[] words = s.toLowerCase().split(" ");
StringBuilder result = new StringBuilder();
for (String word : words) {
    if (word.length() > 0) {
        result.append(Character.toUpperCase(word.charAt(0)))
              .append(word.substring(1)).append(" ");
    }
}
System.out.println(result.toString().trim());
```

---

## 🧪 Ready-to-Practice String Problems (Coming up next)

- Reverse string
- Palindrome check
- First non-repeating char
- Count vowels/consonants
- Anagram check
- Longest common prefix
- Remove duplicates from string
- Check if string is rotation of another
