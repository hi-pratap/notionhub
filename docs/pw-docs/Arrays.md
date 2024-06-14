## Arrays
### Q1. Merge Sorted Array 
```java
   public class MergeTwoSortedArrays {
    public static void main(String[] args) {
        int[] a = {11, 33, 42, 71, 87};
        int[] b = {26, 54, 69, 81, 88, 91};

        int[] c = new int[a.length + b.length];
        int i = 0, j = 0, k = 0;
//main Loop
        while (a.length > i && j < b.length) {
            if (a[i] < b[j]) {
                c[k] = a[i];
                i++;
            } else {
                c[k] = b[j];
                j++;
            }
            k++;
        }
        if (i == a.length) {
            //now take element from b only
            while (j < b.length) {
                c[k] = b[j];
                j++;
                k++;
            }
        }
        if (j == b.length) {
            //now take element from a only
            while (i < a.length) {
                c[k] = a[i];
                i++;
                k++;
            }
        }
//        if(){
//
//        }
        Arrays.stream(c).forEach(System.out::println);
    }
}

   ```
**Problem Understanding**

You have two sorted arrays, `a` and `b`, and you need to merge them into a single sorted array `c`.

**Approach**

The main idea behind merging two sorted arrays efficiently lies in using multiple pointers to traverse through both arrays (`a` and `b`) simultaneously and placing the smaller (or sometimes equal) element into the resulting array (`c`).

 **Step-by-Step Explanation**

1. **Initialization**
   - `int i = 0, j = 0, k = 0;`
     - `i` will be used to iterate through array `a`.
     - `j` will be used to iterate through array `b`.
     - `k` will be used as an index for array `c`, where the merged elements will be placed.

2. **Main Merge Loop**
   ```java
   while (a.length > i && j < b.length) {
       if (a[i] < b[j]) {
           c[k] = a[i];
           i++;
       } else {
           c[k] = b[j];
           j++;
       }
       k++;
   }
   ```
   - This loop continues until either all elements of `a` or all elements of `b` have been processed.
   - It compares the current elements pointed by `i` in `a` and `j` in `b`.
   - If the element in `a` (`a[i]`) is smaller than the element in `b` (`b[j]`), `a[i]` is placed in `c[k]`, and `i` is incremented.
   - Otherwise, `b[j]` is placed in `c[k]`, and `j` is incremented.
   - After placing an element into `c`, `k` is incremented to point to the next position in `c`.

3. **Copying Remaining Elements**
   - After exiting the main merge loop, it's possible that there are remaining elements in either `a` or `b` that haven't been processed.

   ```java
   if (i == a.length) {
       // Copy remaining elements from array b
       while (j < b.length) {
           c[k] = b[j];
           j++;
           k++;
       }
   }
   if (j == b.length) {
       // Copy remaining elements from array a
       while (i < a.length) {
           c[k] = a[i];
           i++;
           k++;
       }
   }
   ```
   - These `if` conditions check whether all elements of `a` or all elements of `b` have been processed (`i == a.length` or `j == b.length`).
   - If `i == a.length`, it means all elements of `a` have been placed in `c`, so the remaining elements of `b` (`b[j]` where `j` ranges from its current position to `b.length - 1`) are copied directly into `c`.
   - If `j == b.length`, it means all elements of `b` have been placed in `c`, so the remaining elements of `a` (`a[i]` where `i` ranges from its current position to `a.length - 1`) are copied directly into `c`.

4. **Output**
   ```java
   Arrays.stream(c).forEach(System.out::println);
   ```
   - Finally, the merged array `c` is printed out using `Arrays.stream(c).forEach(System.out::println);`.

 **Efficiency**

- **Time Complexity:** The time complexity of this approach is \( O(m + n) \), where `m` and `n` are the lengths of arrays `a` and `b` respectively. This is because each element from both arrays `a` and `b` is visited once.
- **Space Complexity:** The space complexity is \( O(m + n) \) due to the additional array `c` created to store the merged result.

 **Conclusion**

Merging two sorted arrays is efficiently achieved using the two-pointer technique, ensuring that the resulting array remains sorted throughout the process. This approach minimizes the number of comparisons needed and ensures optimal performance.

### Q2. Basic Operation On ArrayList
 ```java
public class BasicOperationOnArrayList {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();
        list.add(0, 1);
        list.add(1, 12);
        list.add(2, 13);
        list.add(3, 14);
        list.add(4, 15);
        list.add(5, 16);
        list.set(0, 10);
        System.out.println(list);
    }
}
```

### Q3. Copy Of Array
 ```java
public class CopyOfArray {
    public static void main(String[] args) {
        int[] srudent = {80, 90, 70, 67, 33, 44, 55, 66, 11, 22, 33, 65};
        for (int i : srudent) {
            System.out.print(i+" ");
        }
        int[] nums=srudent; //shallow-copy
        nums[0]=70;
        System.out.println("arr[0]: "+srudent[0]);
        for (int num : nums) {
            System.out.println(num+" ");
        }

        int[ ] deepCopy= Arrays.copyOf(srudent,srudent.length);
        deepCopy[0]=00;
        System.out.println("arr[0]: "+srudent[0]);
        System.out.println("  deepCopy[0]: "+deepCopy[0]);

    }
}

 ```
### Q4. Doublet In Array or TargetSum
```java
public class DoubletInArrayTargetSum {
    public static void main(String[] args) {
        int[] arr = {80, 90, 70, 67, 33, 44, 55, 66, 11, 22, 33, 65};
        int target = 122;
        for (int i = 0; i < arr.length; i++) {

            int remaining = target - arr[i];
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] + arr[j] == target) System.out.println(arr[i] + " " + arr[j]);
            }
        }

    }
}
```
### Q5. Dutch Flag or Sort Colour
```java 
public class DutchFlagSortColour {
    public static void main(String[] args) {
        int[] arr = {0, 1, 0, 2, 2, 1, 2, 0, 1, 0, 2, 0, 2, 1, 2, 1, 2, 1, 0, 0, 0};
        //   methodOneUsingBrutForce(arr);
        methodTwoUsingDutchFlagAlgo(arr);
    }

    private static void methodTwoUsingDutchFlagAlgo(int[] arr) {
        int mid = 0, low = 0;
        int high = arr.length - 1;

        while (mid <= high) {
            if (arr[mid] == 0) {
                //  swapArr(arr[low], arr[mid]);
                int temp = arr[low];
                arr[low] = arr[mid];
                arr[mid] = temp;
                low++;
                mid++;
            } else if (arr[mid] == 1) mid++;
            else if (arr[mid] == 2) {
                //  swapArr(arr[mid], arr[high]);
                int temp = arr[mid];
                arr[mid] = arr[high];
                arr[high] = temp;

                high--;
            }
        }
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }

    }

    private static void swapArr(int i, int j) {
        int temp = i;
        i = j;
        j = temp;
    }

    private static void methodOneUsingBrutForce(int[] arr) {
        int n = arr.length;
        int noOfZeros = 0;
        int noOfOnes = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] == 0) noOfZeros++;
            else if (arr[i] == 1) noOfOnes++;
        }
        int[] ans = new int[n];
        System.out.println("ZerOs: " + noOfZeros + " 1's: " + noOfOnes);
        for (int i = 0; i < n; i++) {
            if (i < noOfZeros) ans[i] = 0;
            else if (i < noOfOnes + noOfZeros) ans[i] = 1;
            else ans[i] = 2;
        }
        for (int i = 0; i < ans.length; i++) {
            System.out.print(ans[i] + " ");
        }
    }
}

```
The logic behind the operations in the Dutch National Flag algorithm, when sorting an array containing elements `0`, `1`, and `2`, is based on partitioning the array into three sections:

1. **Values and Their Positions:**
   - **0:** Should be placed at the beginning of the array.
   - **1:** Should be in the middle section.
   - **2:** Should be placed at the end of the array.

2. **Algorithm Execution:**

   **Initialization:**
   - `low` starts at the beginning of the array (where `0`s will be placed).
   - `mid` starts at the beginning to traverse the array.
   - `high` starts at the end of the array (where `2`s will be placed).

   **Loop Execution:**
   - The algorithm uses a single pass through the array (`mid` traverses from start to end), ensuring `O(n)` time complexity.

   **Conditions and Actions:**
   - **`arr[mid] == 0`:** This means the current element is `0`.
     - Swap `arr[mid]` with `arr[low]` to place `0` in its correct position at the beginning.
     - Increment both `low` and `mid` to move forward.
   
   - **`arr[mid] == 1`:** This means the current element is `1`.
     - No action is needed because `1` should remain in the middle section.
     - Simply increment `mid` to move to the next element.

   - **`arr[mid] == 2`:** This means the current element is `2`.
     - Swap `arr[mid]` with `arr[high]` to place `2` in its correct position at the end.
     - Decrement `high` to move towards the beginning, as the end is correctly sorted.

3. **Result:**
   - After completing the loop, all `0`s are at the beginning, all `1`s are in the middle, and all `2`s are at the end of the array.

 **Key Points:**

- **Efficiency:** The Dutch National Flag algorithm operates in `O(n)` time complexity and `O(1)` space complexity, making it highly efficient.
- **Partitioning:** It partitions the array based on the values `0`, `1`, and `2` by adjusting pointers (`low`, `mid`, `high`) and swapping elements as necessary.
- **Single Pass:** It achieves sorting by examining each element exactly once, ensuring optimal performance for large arrays.

This approach is particularly useful in scenarios where sorting arrays with a small number of distinct values (`0`, `1`, `2`) is required, as it avoids the overhead of traditional sorting algorithms and utilizes minimal extra space.
### Q6. Linear Search
```java
public class LinerSearch {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int target = scanner.nextInt();
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 81, 23, 34, 45, 56, 57, 58};
        boolean flag = false;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                flag = true;
                break;
            }
        }
        if (flag==true) {
            System.out.println("FOund");
        } else System.out.println("Not Found");
    }
}

```
### Q7. maximum Value
```java 
public class MaximumValue {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 81, 23, 34, 45, 56, 57, 58};
        int max = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println(max);
    secondMethod(arr);
    }

    private static void secondMethod(int[] arr) {
        int minValue = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > minValue) {
                minValue = arr[i];
            }
        }
        System.out.println(minValue);
    }

}

```
### Q8. Reverse Array
```java
public class ReverseArray {

    static int[] reverseArrayUsingTwoPointer(int[] arr) {
        int n = arr.length;
        int i = 0, j = n - 1;
        while (i <= j) {
            swap(arr, i, j);
            i++;
            j--;
        }
        System.out.println();
        return arr;
    }

    static int[] reverseArrayUsingFor(int[] arr) {
        for (int i = 0; i < arr.length / 2; i++) {
            int j = arr.length - 1 - i;
            swap(arr, i, j);
        }
        return arr;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    private static void printArray(int[] arr) {
        System.out.println();
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }

    public static void main(String[] args) {
        int[] arr = {80, 90, 70, 67, 33, 44, 55, 66, 11, 22, 33};
        printArray(arr);

        //Method 1: Using Normal For Loop
        // reverseArrayUsingFor(arr);
        //
        // Method 2: Using Two Pointers  //most Optimised
        reverseArrayUsingTwoPointer(arr);

        //Method 3: Using New Array
        // int[] ints = reverseArrayUsingThirdAnotherArray(arr);


        printArray(arr);
        //  printArray(arr);
    }

    private static int[] reverseArrayUsingThirdAnotherArray(int[] arr) {
        int[] ansArr = new int[arr.length];
        int j = 0;
        for (int i = arr.length - 1; i >= 0; i--) {
            ansArr[j++] = arr[i];
        }
        return ansArr;
    }


}

```
### Q9. Rotate Arrays
```java

public class RotateArray {
    public static void main(String[] args) {
        int[] arr = {80, 90, 70, 67, 33, 44, 55, 66, 11, 22, 33};
        for (int i : arr) {
            System.out.print(i + " ");
        }

        int n = arr.length;
        int k = 2;
        // int i = 1, j = n - 3;

        reverse(arr, 0, n - k - 1);
        reverse(arr, n - k, n - 1);
        reverse(arr, 0, n - 1);
        System.out.println();
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }

    private static void reverse(int[] arr, int i, int j) {
        while (i <= j) {
            swap(arr, i, j);
            i++;
            j--;
        }
    }
/*
*
 Reverse First Part of the Array

----------------reverse(nums, 0, n - k - 1);

This line calls the reverse method to reverse the first part of the array, from the start (0) to the index n - k - 1.

Reverse Second Part of the Array

---------------reverse(nums, n - k, n - 1);

*This line calls the reverse method to reverse the second part of the array, from the index n - k to the end of the array (n - 1).

Reverse the Entire Array

----------------reverse(nums, 0, n - 1);
This line calls the reverse method to reverse the entire array from the start (0) to the end (n - 1). After this step, the array will be rotated by k positions.

* */

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

```
### Q2. Second Largest
```java

public class SecondLargest {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 81, 23, 34, 45, 56, 57, 58};
        myWay(arr);
        usingStream(arr);
    }

    private static void usingStream(int[] arr) {

        Arrays.stream(arr).boxed().sorted((a,b)->b-a).skip(1).limit(1).forEach(System.out::println);
    }

    private static void myWay(int[] arr) {
        int max = Integer.MIN_VALUE;
        int secondMax = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) max = arr[i];
            else if (arr[i] > secondMax && arr[i] != max) secondMax = arr[i];

        }
        System.out.println(max + " " + secondMax);
    }
}

```
### Q2. Sort Zeroes and Ones
```java 
public class SortZerosAndOnes {
    public static void main(String[] args) {
//        int[] arr = {0, 0, 1, 0, 1, 1, 1, 0, 1, 0};
     int[] arr = {0, 0,0,0,0, 1, 1, 1, 1};
        int n = arr.length;
        // twoPassSolution(n, arr);
        onePassSolution(n, arr);

//        Arrays.stream(arr).forEach(System.out::print);
        for (int ele : arr) {
            System.out.print(ele+" ");
        }
    }

    private static void onePassSolution(int n, int[] arr) {
        // Initialize two pointers: i= starting from the beginning of the array and j= starting from the end
        int i = 0, j = n - 1;

        // Loop until the two pointers meet
        while (i < j) {
            // If the element at i is already 0, move the i pointer to the right
            if (arr[i] == 0) i++;

            // If the element at j is already 1, move the j pointer to the left
            else if (arr[j] == 1) j--;

            // If the element at i is 1 and the element at j is 0, swap them
            else if (arr[i] == 1 && arr[j] == 0) {
                arr[i] = 0;
                arr[j] = 1;
                i++;         // Move the i pointer to the right
                j--;         // Move the j pointer to the left
            }
        }
    }



    private static void twoPassSolution(int n, int[] arr) {
        int noOfZeroes = 0, noOdOnes = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] == 0) noOfZeroes++;
            //  else noOdOnes++;
        }
        for (int i = 0; i < n; i++) {
            if (i < noOfZeroes) arr[i] = 0;
            else arr[i] = 1;
        }
       /* for (int i = noOfZeroes; i < n; i++) {
            arr[i] = 1;
        }*/
    }
}
```
### Q2.
### Q2.
### Q2.
### Q2.
### Q2.
### Q2.
### Q2.
### Q2.
### Q2.
 ### Q2.
 