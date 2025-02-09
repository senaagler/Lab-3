# Lab-3
Animals
package Lab9;

import java.util.ArrayList;




abstract class Animal {
    int age;
    String gender;

    public Animal(int age, String gender) {
        this.age = age;
        this.gender = gender;
    }

    public abstract void voice();

    public final void sleep() {
        System.out.println("Sleeping...");
    }

    public abstract boolean isMammal();

    public abstract String toString();
}




class Duck extends Animal {
    String beakColor;

    public Duck(int age, String gender, String beakColor) {
        super(age, gender);
        this.beakColor = beakColor;
    }

    public void swim() {
        System.out.println("Duck is swimming...");
    }

    public void quack() {
        System.out.println("Duck is quacking...");
    }

    @Override
    public void voice() {
        System.out.println("Duck says quack!");
    }

    @Override
    public boolean isMammal() {
        return false;
    }

    @Override
    public String toString() {
        return "Duck [age=" + age + ", gender=" + gender + ", beakColor=" + beakColor + ", isMammal=" + isMammal() + "]";
    }
}







class Fish extends Animal {
    int sizeInFt;
    boolean canEat;

    public Fish(int age, String gender, int sizeInFt, boolean canEat) {
        super(age, gender);
        this.sizeInFt = sizeInFt;
        this.canEat = canEat;
    }

    public void swim() {
        System.out.println("Fish is swimming...");
    }

    @Override
    public void voice() {
        System.out.println("Fish makes no sound!");
    }

    @Override
    public boolean isMammal() {
        return false;
    }

    @Override
    public String toString() {
        return "Fish [age=" + age + ", gender=" + gender + ", sizeInFt=" + sizeInFt + ", canEat=" + canEat + ", isMammal=" + isMammal() + "]";
    }
}





class Zebra extends Animal {
    boolean isWild;

    public Zebra(int age, String gender, boolean isWild) {
        super(age, gender);
        this.isWild = isWild;
    }

    public void run() {
        System.out.println("Zebra is running...");
    }

    @Override
    public void voice() {
        System.out.println("Zebra says neigh!");
    }

    @Override
    public boolean isMammal() {
        return true;
    }

    @Override
    public String toString() {
        return "Zebra [age=" + age + ", gender=" + gender + ", isWild=" + isWild + ", isMammal=" + isMammal() + "]";
    }
}






public class Lab9 {
    public static void main(String[] args) {
        ArrayList<Animal> animals = new ArrayList<>();

        animals.add(new Animal(2, "Male") {
            @Override
            public void voice() {
                System.out.println("Generic Animal Sound");
            }

            @Override
            public boolean isMammal() {
                return true;
            }

            @Override
            public String toString() {
                return "Animal [age=" + age + ", gender=" + gender + ", isMammal=" + isMammal() + "]";
            }
        });

        animals.add(new Duck(1, "Female", "yellow"));
        animals.add(new Duck(2, "Male", "yellow"));
        animals.add(new Duck(3, "Female", "yellow"));
        animals.add(new Fish(1, "Male", 2, true));
        animals.add(new Fish(2, "Female", 1, false));
        animals.add(new Zebra(5, "Male", true));
        animals.add(new Zebra(4, "Female", false));
        animals.add(new Zebra(6, "Male", true));
        animals.add(new Zebra(3, "Female", false));

        for (Animal animal : animals) {
            System.out.println(animal.toString());
            animal.voice();
            animal.sleep();

            if (animal instanceof Duck) {
                ((Duck) animal).swim();
                ((Duck) animal).quack();
            } else if (animal instanceof Fish) {
                ((Fish) animal).swim();
            } else if (animal instanceof Zebra) {
                ((Zebra) animal).run();
            }
            System.out.println("---------------------------");
        }
    }
}
