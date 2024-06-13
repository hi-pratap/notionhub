# Basics:

### Q1. Area Of Circle?

```java
public class AreaOfCircle {
    public static void main(String[] args) {
        double valueOfPie=3.141592;
        double radius=3.7;

        double areaOfCircle=valueOfPie*radius*radius;
        System.out.println("Area of circle is : "+areaOfCircle);
    }
}
```

### Q2. Simple Interest

```java
public class SimpleInterest {
    public static void main(String[] args) {
        double principle=2000;
        double rate=3.75;
        double time=3.5;

        double si=(principle*rate*time)/100;
        System.out.println("Simple Interest is: "+si);

    }
}

```

### Q3. Volume of Sphere

```java
public class VolumeOfSphere {
    public static void main(String[] args) {
        double radius=4.8;
        double r=(4*3.1415*radius*radius*radius)/3;
        System.out.println(r);

    }
}

```