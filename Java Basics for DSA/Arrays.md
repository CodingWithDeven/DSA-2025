
# 📚 Arrays in Java — From Basics to Advanced 🚀

---

## 🔰 What is an Array?
An array is a **fixed-size container** that holds values of the **same type**, like a row of lockers.

### ✅ Example:
```java
int[] numbers = {10, 20, 30, 40};
System.out.println(numbers[2]); // prints 30
```

### 🛠️ Declaring & Initializing
```java
int[] arr;                 // declaration
arr = new int[5];          // initialize with size 5 (defaults to 0)
int[] scores = {95, 88, 76}; 
String[] names = new String[]{ "Alice", "Bob" };
```

## 📐 Key Properties of Arrays
- Fixed size — can't resize after creation
- Zero-based indexing
- Supports both primitives and objects
- Stored in contiguous memory

## 🧰 Useful Arrays Utility Methods
```java
import java.util.Arrays;

Arrays.sort(arr);                    // Sort in-place
Arrays.toString(arr);                // Print array
Arrays.equals(a, b);                 // Compare arrays
Arrays.copyOf(arr, newSize);         // Resize
Arrays.binarySearch(arr, key);       // Binary search (sorted only)
Arrays.fill(arr, value);             // Fill array with value
```

## 🚀 Set & HashMap in Arrays — Powerful Tools

### 🧾 When to Use a Set
- ✅ Check for existence in O(1)
- ✅ Remove duplicates
- ✅ Find if a pair like x & -x exists
- ✅ Count unique elements

### 🧾 When to Use a HashMap
- ✅ Count frequency of elements
- ✅ Find first non-repeating element
- ✅ Track indices or previous positions
- ✅ Manage key-value relationships

### 🧺 Set Examples

#### 1. Check for Duplicates
```java
Set<Integer> seen = new HashSet<>();
for (int num : arr) {
    if (!seen.add(num)) {
        System.out.println("Duplicate: " + num);
    }
}
```

#### 2. Find Max Number Where Both x and -x Exist
```java
Set<Integer> set = new HashSet<>();
int max = -1;
for (int num : arr) {
    if (set.contains(-num)) {
        max = Math.max(max, Math.abs(num));
    }
    set.add(num);
}
```

### 📊 HashMap Examples

#### 1. Frequency Count
```java
Map<Integer, Integer> freq = new HashMap<>();
for (int num : arr) {
    freq.put(num, freq.getOrDefault(num, 0) + 1);
}
System.out.println(freq);
```

#### 2. First Non-Repeating Element
```java
for (int num : arr) {
    freq.put(num, freq.getOrDefault(num, 0) + 1);
}
for (int num : arr) {
    if (freq.get(num) == 1) {
        System.out.println("First unique: " + num);
        break;
    }
}
```

#### 3. Two Sum Using HashMap
```java
Map<Integer, Integer> map = new HashMap<>();
for (int i = 0; i < arr.length; i++) {
    int complement = target - arr[i];
    if (map.containsKey(complement)) {
        System.out.println("Pair: " + arr[i] + " and " + complement);
        break;
    }
    map.put(arr[i], i);
}
```

## 🎯 Two-Pointer Technique — Game On!

### 🧠 When to Use:
- Process both ends
- Find pairs (e.g., 2-sum)
- Rearrangement or partitioning
- In-place filtering/removal

### 🚦 Pointer Start Positions
| Pattern              | Start Pointers     | Use Case                      |
|----------------------|--------------------|-------------------------------|
| Both ends            | i = 0, j = n-1      | Reverse, 2-sum, palindrome     |
| Neighbor pairs       | i = 0, j = i+1      | All pair comparisons          |
| Read–write (slow-fast)| i = 0, j = 0       | Remove/filter elements in-place|
| Swap & shrink        | i = 0, j = n-1      | Even/odd, zero shifting        |

### 🔄 Common Two-Pointer Code Snippets

#### 1. Reverse Array
```java
for (int i = 0, j = arr.length-1; i < j; i++, j--) {
    int tmp = arr[i];
    arr[i] = arr[j];
    arr[j] = tmp;
}
```

#### 2. Remove Duplicates (Sorted)
```java
int i = 0;
for (int j = 1; j < arr.length; j++) {
    if (arr[j] != arr[i]) {
        i++;
        arr[i] = arr[j];
    }
}
// Unique length = i + 1
```

#### 3. Two Sum in Sorted Array
```java
int left = 0, right = arr.length - 1;
while (left < right) {
    int sum = arr[left] + arr[right];
    if (sum == target) break;
    else if (sum < target) left++;
    else right--;
}
```

#### 4. Move Zeros to End
```java
int i = 0;
for (int j = 0; j < arr.length; j++) {
    if (arr[j] != 0) {
        int tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
        i++;
    }
}
```

#### 5. Partition Even/Odd
```java
int left = 0, right = arr.length - 1;
while (left < right) {
    while (left < right && arr[left] % 2 == 0) left++;
    while (left < right && arr[right] % 2 != 0) right--;
    if (left < right) {
        int tmp = arr[left];
        arr[left++] = arr[right];
        arr[right--] = tmp;
    }
}
```

## 🎓 Arrays in Advanced Java

### Multi-dimensional Arrays
```java
int[][] matrix = {
  {1, 2, 3},
  {4, 5, 6}
};
System.out.println(matrix[1][2]); // 6
```

### Jagged Arrays (Uneven Rows)
```java
int[][] jagged = new int[3][];
jagged[0] = new int[2];
jagged[1] = new int[4];
jagged[2] = new int[1];
```

### Arrays of Objects
```java
String[] names = { "Alice", "Bob" };
Employee[] staff = new Employee[10];
```

## ⚖️ Arrays vs ArrayList
| Feature      | Array     | ArrayList        |
|--------------|-----------|------------------|
| Fixed Size   | ✅ Yes    | ❌ No            |
| Primitives   | ✅ Yes    | ❌ No            |
| Performance  | ✅ Fast   | ⚠️ Slight overhead |
| Methods      | Basic only | Rich utility    |

## 🧠 Common Mistakes to Avoid
- ❌ Using arr.length() → It should be arr.length (no ())
- ❌ ArrayIndexOutOfBoundsException → Always check bounds
- ❌ Infinite loop in two-pointer → Update both pointers correctly
- ❌ Swapping logic wrong → Always update positions after swap
- ❌ Object comparison → Use .equals() not == for strings/objects