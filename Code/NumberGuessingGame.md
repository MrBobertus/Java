```
// Importing Stuff like a Input Scanner
import java.util.Random;
import java.util.Scanner;

public class Main {

    // --- --- --- > Settings < --- --- --- \\

    public static int minNumber = 1;
    public static int maxNumber = 100;
    public static int triesAmount = 5;

    // --- - --- > End of Settings --- - --- \\

    // --- DO NOT CHANGE ANYTHING BEYOND THIS IF YOU DON'T KNOW WHAT YOU ARE DOING --- \\

    // Game Variables like "Is the game Running"
    public static boolean running = false;
    public static int currentTries = 0;

    // Logic Method / Function which checks how many tries the Player has left and if he got the correct Number
    public static void logic(int input, int triesAmount, int randomNumber) {

        currentTries += 1;

        if (input == randomNumber) {
            running = false;
            System.out.println("Thats correct...");
        } else if (currentTries == triesAmount) {
            running = false;
            System.out.println("No tries left...");
        } else if (input < randomNumber) {
            System.out.println("A bit higher...");
            System.out.println("You have " + (triesAmount - currentTries) + " tries left...");
        } else if (input > randomNumber) {
            System.out.println("A bit lower...");
            System.out.println("You have " + (triesAmount - currentTries) + " tries left...");
        }
    }

    // Main Method / Function which will be executed at the beginning (A Java thing...)
    public static void main(String[] args) {
        // Instantiate Objects like random for random number and scanner for the input
        Random random = new Random();
        Scanner scanner = new Scanner(System.in);

        System.out.println("Thinking of a Number...");
        int randomNumber = random.nextInt(minNumber, maxNumber);
        System.out.println("Now try to guess my number with " + triesAmount + " tries...");
        running = true;

        // Main Game Loop
        do {
            int input = scanner.nextInt();

            // Calling Logic Method / Function
            logic(input, triesAmount, randomNumber);
        } while (running && currentTries != triesAmount);

        System.out.println("My Number was " + randomNumber);
    }
}
```
