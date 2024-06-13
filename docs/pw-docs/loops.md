# Loops

### Q.1 Even Odd

```java
public class AllEvenAndOdd {
    public static void main(String[] args) {
        System.out.println("All even");

        //100 round
        int count = 0;
        for (int i = 1; i <= 100; i++) {
            System.out.println(count++);
            if (i % 2 == 0) System.out.println(i + " Even");
        }
        //50 round
        count = 0;
        for (int i = 2; i <= 100; i += 2) {
            System.out.println(count++);
            if (i % 2 == 0) System.out.println(i + " Even");
        }
    }
}
```

### Q.2 Arithematic Progression

```java
public class ArithematicProgression {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("ENter N: ");
        int i1 = scanner.nextInt();
        //1 3 5 7 9

        for (int i = 1; i <= 2 * i1 - 1; i += 2) {
            System.out.println(i);
        }
        System.out.println("Without Math");
        int a = 1;
        for (int i = 1; i <=i1; i ++) {
            System.out.println(a);
            a -= 2;
        }

        System.out.println("Geometric  Math");
        int ab= 1,d=4;
        for (int i = 1; i <=i1; i ++) {
            System.out.println(ab);
            ab *= d;
        }
    }
}
```

### Q2. Composite Number

```java
public class CheckNumberComposite {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a Number n: ");
        int n = scanner.nextInt();
        int x = 0; // prime
        for (int j = 2; j < n - 1; j++) {
            if (n % j == 0) {
                System.out.println(n + " is a Composite Number");
                x = 1;// composite
                break;
            }
        }
        if (n == 1) System.out.println("Neither Prime nor Composite");
        else if (x == 0) System.out.println("prime Number");
    }
}

```