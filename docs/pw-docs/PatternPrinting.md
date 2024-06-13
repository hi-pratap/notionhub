# Pattern Printing

## Squares

### Q1. Number Printing

```java
public class NumberPrinting {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int row = scanner.nextInt();
        int col = scanner.nextInt();
        for (int i = 1; i <= row; i++) {
            for (int j = 1; j <= col; j++) {

                System.out.print((char) (j + 64) + " ");
            }
            System.out.println();
        }
    }
}

//output
A B C D 
A B C D 
A B C D 
A B C D 
A B C D 
```

### Q.2 Star Square

```java
public class PatternPrinting {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int row = scanner.nextInt();
        int col = scanner.nextInt();
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}

//output
* * * * * * 
* * * * * * 
* * * * * * 
* * * * * * 
* * * * * * 
* * * * * * 
```

## Triangles_Composite

### Q.1 Number Bridge

```java
public class NumberBridge {
    public static void main(String[] args) {
        int n = 5;

        for (int i = 1; i <= 2 * n - 1; i++) System.out.print(i + " ");
        System.out.println();
        n--;
        for (int i = 1; i <= n; i++) {
            int a = 1;
            for (int j = 1; j <= n + 1 - i; j++) { //number
                System.out.print(a++ + " ");
            }
            for (int j = 1; j <= 2 * i - 1; j++) {
                a++;
                System.out.print(" " + " ");
            }
            for (int j = 1; j <= n + 1 - i; j++) {
                System.out.print(a++ + " ");
            }
            System.out.println();
        }
    }
}

//Output
1 2 3 4 5 6 7 8 9 
1 2 3 4   6 7 8 9 
1 2 3       7 8 9 
1 2           8 9 
1               9 

```

### Q.2 Number Flipped

```java
public class NumberFlipped {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= 5 - i; j++) {
                System.out.print(" " + " ");
            }

            for (int j = 1; j <= i; j++) {
                System.out.print(j + " ");
            }
            System.out.println();
        }
    }
}
//output
        1 
      1 2 
    1 2 3 
  1 2 3 4 
1 2 3 4 5 
```

### Q.3 Number Pyramid Palindrome

```java
public class NumberPyramidPalindrome {
    public static void main(String[] args) {

            int n = 5;
            for (int i = 1; i <= n; i++) {
                for (int j = 1; j <= n - i; j++) { //spaces
                    System.out.print(" " + " ");
                }
                for (int j = 1; j <=  i; j++) { //starts
                  System.out.print(j+ " ");
                }

                for (int j = i-1; j >= 1; j--) { //starts
                  System.out.print(j+ " ");
                }
                System.out.println();
            }

    }
}
//output
        1 
      1 2 1 
    1 2 3 2 1 
  1 2 3 4 3 2 1 
1 2 3 4 5 4 3 2 1 
```

### Q.4 Pyramid Composite

```java
public class PyramidComposite {
    public static void main(String[] args) {
        int n = 16;
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n - i; j++) { //spaces
                System.out.print(" " + " ");
            }
            for (int j = 1; j <= 2 * i - 1; j++) { //starts
                System.out.print("*" + " ");
            }
            System.out.println();
        }
    }
}
//Output
                              * 
                            * * * 
                          * * * * * 
                        * * * * * * * 
                      * * * * * * * * * 
                    * * * * * * * * * * * 
                  * * * * * * * * * * * * * 
                * * * * * * * * * * * * * * * 
              * * * * * * * * * * * * * * * * * 
            * * * * * * * * * * * * * * * * * * * 
          * * * * * * * * * * * * * * * * * * * * * 
        * * * * * * * * * * * * * * * * * * * * * * * 
      * * * * * * * * * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * * * * * * * * * * * 
  * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
```

### Q.5 Rhombus Traingle

```java
public class RhombusTriangle {
    public static void main(String[] args) {
        int n = 6;
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n - i; j++) {
                System.out.print("0" + " ");
            }
            for (int j = 1; j <= n; j++) {
                System.out.print("*" + " ");
            }
            System.out.println();
        }
    }

}

//output 
          * * * * * * 
        * * * * * * 
      * * * * * * 
    * * * * * * 
  * * * * * * 
* * * * * * 
```