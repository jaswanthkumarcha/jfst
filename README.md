# jfst


#2)What is the result when one tries to compile and run the following code?
public final static void main(String[] args){
double d = 10.0 / -0;
if(d == Double.POSITIVE_INFINITY)
 System.out.println("Positive infinity");
else
System.out.println("Negative infinity");
}
#output:
Negative infinity

#3)public void foo(ArrayList<String> data)
{
 //some code
}
public void foo (ArrayList<Integer> data)
{
 //some code
}
public ArrayList<String> foo (ArrayList<String> data)
{
 //some code
}
private void foo(List<String> data)
{
 //some code
}
public void foo(ArrayList<String> data, boolean flag)
{
 //some code
}
#output:
"'foo(ArrayList)' clashes with 'foo(ArrayList)

abstract class Food {
    double proteins;
    double fats;
    double carbs;
    double tastyScore;
    
    abstract void getMacroNutrients();
}

class Egg extends Food {
    int tastyScore = 7;
    String type = "non-vegetarian";
    
    Egg(double proteins, double fats, double carbs) {
        this.proteins = proteins;
        this.fats = fats;
        this.carbs = carbs;
    }
    
    void getMacroNutrients() {
        System.out.println("An egg has " + this.proteins + " gms of protein, " +
                           this.fats + " gms of fats and " + this.carbs + " gms of carbohydrates.");
    }
}

class Bread extends Food {
    int tastyScore = 8;
    String type = "vegetarian";
    
    Bread(double proteins, double fats, double carbs) {
        this.proteins = proteins;
        this.fats = fats;
        this.carbs = carbs;
    }
    
    void getMacroNutrients() {
        System.out.println("A slice of bread has " + this.proteins + " gms of protein, " +
                           this.fats + " gms of fats and " + this.carbs + " gms of carbohydrates.");
    }
}
#output:
An egg has 6.3 gms of protein, 5.3 gms of fats and 0.6 gms of
carbohydrates.
Taste: 7
Egg is non-vegetarian

#abstract class Calculator {
    abstract int add(int a, int b);
}

class Adder extends Calculator {
    @Override
    int add(int a, int b) {
        System.out.println("Adding integers: " + a + " " + b);
        return a + b;
    }
}

class Multiplier {
    int multiply(int a, int b, Calculator calculator) {
        int result = 0;
        for (int i = 0; i < b; i++) {
            result = calculator.add(result, a);
        }
        return result;
    }
}

public class Solution {
    public static void main(String[] args) {
        Adder adder = new Adder();
        Multiplier multiplier = new Multiplier();

        int a = 7;
        int b = 4;

        System.out.println("Testing Addition");
        int sum = adder.add(a, b);
        System.out.println("Sum = " + sum);

        System.out.println("Testing Multiplication");
        int product = multiplier.multiply(a, b, adder);
        System.out.println("Product = " + product);
    }
}
#output:
Testing Addition
Adding integers: 7 4
Sum = 11
Testing Multiplication
Adding integers: 0 7
Adding integers: 7 7
Adding integers: 14 7
Adding integers: 21 7
Product = 28
6)
class Acquaintance {
    String name;

    Acquaintance(String name) {
        this.name = name;
    }

    public void getStatus() {
        System.out.println(name + " is just an acquaintance.");
    }
}

class Friend extends Acquaintance {
    String homeTown;

    Friend(String name, String homeTown) {
        super(name);
        this.homeTown = homeTown;
    }

    @Override
    public void getStatus() {
        System.out.println(name + " is a friend and he is from " + homeTown + ".");
    }
}

class BestFriend extends Friend {
    String favoriteSong;

    BestFriend(String name, String homeTown, String favoriteSong) {
        super(name, homeTown);
        this.favoriteSong = favoriteSong;
    }

    @Override
    public void getStatus() {
        System.out.println(name + " is my best friend. He is from " + homeTown +
                           " and his favorite song is " + favoriteSong + ".");
    }
}

public class Main {
    public static void main(String[] args) {
        // Sample input
        Acquaintance acquaintance = new Acquaintance("Jaden");
        acquaintance.getStatus();

        Friend friend1 = new Friend("Jake", "Florida");
        friend1.getStatus();

        BestFriend bestFriend = new BestFriend("Ryan", "Utah", "Dangerous");
        bestFriend.getStatus();

        Friend friend2 = new Friend("David", "Texas");
        friend2.getStatus();
    }
}
#output...
Jaden is just an acquaintance.
Jake is a friend and he is from Florida.
Ryan is my best friend. He is from Utah and his favorite song is Dangerous.
David is a friend and he is from Texas.
8)abstract class Car {
    abstract boolean getIsSedan();
    abstract int getSeats();
    abstract String getMileage();
}

class WagonR extends Car {
    private int mileage;

    WagonR(int mileage) {
        this.mileage = mileage;
    }

    @Override
    boolean getIsSedan() {
        return false;
    }

    @Override
    int getSeats() {
        return 4;
    }

    @Override
    String getMileage() {
        return mileage + " kmpl";
    }
}

class HondaCity extends Car {
    private int mileage;

    HondaCity(int mileage) {
        this.mileage = mileage;
    }

    @Override
    boolean getIsSedan() {
        return true;
    }

    @Override
    int getSeats() {
        return 4;
    }

    @Override
    String getMileage() {
        return mileage + " kmpl";
    }
}

class InnovaCrysta extends Car {
    private int mileage;

    InnovaCrysta(int mileage) {
        this.mileage = mileage;
    }

    @Override
    boolean getIsSedan() {
        return false;
    }

    @Override
    int getSeats() {
        return 6;
    }

    @Override
    String getMileage() {
        return mileage + " kmpl";
    }
}

public class Main {
    public static void main(String[] args) {
        int type = Integer.parseInt(args[0]);
        int mileage = Integer.parseInt(args[1]);

        Car car;

        if (type == 0) {
            car = new WagonR(mileage);
        } else if (type == 1) {
            car = new HondaCity(mileage);
        } else {
            car = new InnovaCrysta(mileage);
        }

        String sedanStatus = car.getIsSedan() ? "Sedan" : "not Sedan";
        int seats = car.getSeats();
        String carMileage = car.getMileage();

        System.out.println("A " + car.getClass().getSimpleName() + " is " + sedanStatus +
                           ", is " + seats + "-seater, and has a mileage of around " +
                           carMileage + ".");
    }
}
output:
Sample output for input (1, 12) (indicating a HondaCity with mileage 12):

csharp
Copy code
A HondaCity is Sedan, is 4-seater, and has a mileage of around 12 kmpl.

