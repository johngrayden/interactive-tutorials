Tutorial
--------

Inheritence in Java allows you to reuse code from an existing class into another class,
you can `derive` your new class from an existing class. Your new class is called `derived`
class which inherits all the members from its superclass.

The inherited fields can be used directly, just like any other fields.
You can declare a field in the subclass with the same name as the one in the superclass, thus hiding it (not recommended).
You can declare new fields in the subclass that are not in the superclass.
The inherited methods can be used directly as they are.
You can write a new instance method in the subclass that has the same signature as the one in the superclass, thus overriding it.
You can write a new static method in the subclass that has the same signature as the one in the superclass, thus hiding it.
You can declare new methods in the subclass that are not in the superclass.
You can write a subclass constructor that invokes the constructor of the superclass, either implicitly or by using the keyword super.
A subclass does not inherit the private members of its parent class.


### An example of inheritence

Consider a class called Shape, Shape is the base class which is inherited by shapes like rectangle, square, circle etc.

    public class Shape {
        public double area ()
        {
            return 0;     // Since this is just a generic "Shape" we will assume the area as zero.
                        // The actual area of a shape must be overridden by a subclass, as we see below.
                        // You will learn later that there is a way to force a subclass to override a method,
                        // but for this simple example we will ignore that.
        }
    }
  
  
Class `Shape` is inherited by Circle which is a Shape.

The method area is defined in the base class and has been inherited in the circle class and
method `area` is available with the circle class which is redefined specific to circle.

  
    class Circle extends Shape {                    // The "extends" keyword is what we use to tell java that Circle inherits the functionality of Shape.
  
        private static final double PI = Math.PI;   // constant
        private double diameter;                    // This could be any number, representing the diameter of this circle.
    
        public double area () {
            double radius = diameter / 2.0;
            return PI * radius * radius;
        }
  
    }
  
The advantage of using inheritance is that you can write code that can apply to a number of classes that extend a more general class.  In the below example we have a method that takes the larger area from the two shapes:

    public class Main {
        public static void main(String[] args) {
            Shape s1 = new Circle (5.0);
            Shape s2 = new Rectangle (5.0, 4.0);
            Shape larger = getLargerShape(s1,s2);
            
            System.out.println("The area of the larger shape is: "+larger.area());
        }
        
        public static Shape getLargerShape(Shape s1, Shape s2) {
            if(s1.area() > s2.area()) {
                return s1;
            } else {
                return s2;
            }
        }
    }

As you can see, `getLargerShape()` doesn't require the programmer to input a specific type of shape for its 2 parameters.  You could use an instance of any class that inherits the type `Shape` as any of the two parameters
for this method.  You could use an instance of type `Circle`, `Rectangle`, `Triangle`, `Trapezoid`, etc. - as long as they `extend Shape`.

Exercise
--------

Create a rectangle class which inherits the Shape class and finds the area

Tutorial Code
-------------

    class Shape {
        public double area ()
        {
            return 0;     // Since this is just a generic "Shape" we will assume the area as zero.
                        // The actual area of a shape must be overridden by a subclass, as we see below.
                        // You will learn later that there is a way to force a subclass to override a method,
                        // but for this simple example we will ignore that.
        }
    }


    class Circle extends Shape {                    // class declaration
        Circle (double diameter) {                  // constructor
            this.diameter = diameter;
        }
        private static final double PI = Math.PI;   // constant
        private double diameter;                    // instance variable
        
        public double area () {                     // dynamic method
            double radius = diameter / 2.0;
            return PI * radius * radius;
        }

    }


    class Rectangle extends Shape {
        // Your code goes here

    }


    public class Main {
        public static void main(String[] args) {
            Shape s1 = new Circle (2.5);
            Shape s2 = new Rectangle (5.0, 4.0);
            
            System.out.println (s1.area());
            System.out.println (s2.area());
        }
    }

Expected Output
---------------

4.908738521234052
20.0

Solution
--------

    class Shape {
        public double area ()
        {
            return 0;     // Since this is just a generic "Shape" we will assume the area as zero.
                        // The actual area of a shape must be overridden by a subclass, as we see below.
                        // You will learn later that there is a way to force a subclass to override a method,
                        // but for this simple example we will ignore that.
        }
    }

    class Circle extends Shape {                    // class declaration
        Circle (double diameter) {                  // constructor
            this.diameter = diameter;
        }
        private static final double PI = Math.PI;   // constant
        private double diameter;                    // instance variable
        
        public double area () {                     // dynamic method
            double radius = diameter / 2.0;
            return PI * radius * radius;
        }

    }

    class Rectangle extends Shape {
        Rectangle (double width, double height) {
            this.width = width;
            this.height = height;
        }
        
        private double width;        // length of one side
        private double height;        // length of the other side
        
        public double area () {
            return width * height;
        }

    }

    public class Main {
        public static void main(String[] args) {
            Shape s1 = new Circle (2.5);
            Shape s2 = new Rectangle (5.0, 4.0);
            
            System.out.println (s1.area());
            System.out.println (s2.area());
        }
    }
