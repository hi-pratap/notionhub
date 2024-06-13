# Conditionals:

### Q.1 Check 3 Digit Number

```java
public class Check3DigitNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int i = scanner.nextInt();
        if (i > 99 && i < 1000) System.out.println("three digit number");
        else System.out.println("Not three digit number");

    }
}
```

### Q.2 EvenOdd

```java
public class EvenOdd {
    public static void main(String[] args) {

        Scanner scanner=new Scanner(System.in);
        System.out.print("Enter the Number: ");
        int i = scanner.nextInt();

        if(i%2==0) System.out.println("Number is even");
        else System.out.println("Not even");
    }
}

```

### Q.3 Greatest Of Three

```java
public class GreatestOfThree {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int a = scanner.nextInt();
        int b = scanner.nextInt();
        int c = scanner.nextInt();

        if (a >= b && a >= c) System.out.println("Greater A " + a);
        else if (b >= a && b >= c) System.out.println("Greater B " + b);
        else System.out.println("Greater c " + c);

        if (a <= b && a <= c) System.out.println("less A " + a);
        else if (b <= a && b <= c) System.out.println("less B " + b);
        else System.out.println("less c " + c);

        System.out.println("Without Using && :");

        if (a > b) {
            if (a > c) {
                System.out.println(a + " is Largest");
            } else {
                System.out.println(c + " is Largest");
            }
        } else {
            if (b > c) {
                System.out.println(b + " is Largest");
            } else {
                System.out.println(c + " is Largest");
            }
        }
    }
}

```

### Q.4 Profit Loss

```java
public class ProfitLoss {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter cost price: ");
        int cp = sc.nextInt();
        System.out.print("Enter Selling price : ");
        int sp = sc.nextInt();
        if (cp < sp) System.out.println("Profit"+(sp-cp));
        if (cp > sp) System.out.println("Loss"+(cp-sp));
        if (cp == sp) System.out.println("No Loss, No profit");
    }
}

```

### Q.5 Quadrant

```java
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter x and y: ");
        int y = scanner.nextInt();
        int x = scanner.nextInt();

        if (x > 0 && y > 0)
            System.out.println("First Quadrant");
        else if (x < 0 && y < 0)
            System.out.println("Third Quadrant");
        else if (x < 0 && y > 0)
            System.out.println("Second Quadrant");
        else if (x > 0 && y < 0) System.out.println("Fourth Quadrant");
        else System.out.println("center");

    }
}
```

### Q.6 Rectangle Perimeter

```java
public class RectanglePerimeter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter The lenghth: ");
        int l = scanner.nextInt();
        System.out.println("Enter The Breadth: ");
        int b = scanner.nextInt();
        int area = l * b;
        int perimerter = 2 * (l * b);
        if (area > perimerter) System.out.println("area is greater");
        if (area < perimerter) System.out.println("area is small");
    }
}
```

### Q.7 Triangle or not

```java
public class TriangleOrNot {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter 1st side: ");
        int a = sc.nextInt();
        System.out.print("Enter 2st side: ");
        int b = sc.nextInt();
        System.out.print("Enter 3st side: ");
        int c = sc.nextInt();

        if (((a + b) > c) && ((b + c) > a) && ((c + a) > b)) {
            System.out.println("Its a Triangle...!!!!!!");
        } else System.out.println("Not a Triangle... !!!");

    }
}
```