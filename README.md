# CODESOFT
Code1

import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        int roundsPlayed = 0;
        int roundsWon = 0;
        boolean playAgain = true;
        
        while (playAgain) {
            int targetNumber = random.nextInt(100) + 1;
            int attempts = 0;
            boolean guessedCorrectly = false;
            final int maxAttempts = 10;

            System.out.println("Welcome to the Number Guessing Game!");
            System.out.println("You have " + maxAttempts + " attempts to guess the number between 1 and 100.");
            
            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess (attempt " + (attempts + 1) + "): ");
                int guess = scanner.nextInt();
                attempts++;
                
                if (guess < targetNumber) {
                    System.out.println("Too low! Try again.");
                } else if (guess > targetNumber) {
                    System.out.println("Too high! Try again.");
                } else {
                    System.out.println("Congratulations! You guessed the correct number.");
                    guessedCorrectly = true;
                    roundsWon++;
                }
            }
            
            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all your attempts. The correct number was " + targetNumber + ".");
            }
            
            roundsPlayed++;
            
            System.out.print("Do you want to play another round? (yes/no): ");
            playAgain = scanner.next().equalsIgnoreCase("yes");
        }
        
        System.out.println("Game Over! You played " + roundsPlayed + " rounds and won " + roundsWon + " rounds.");
        
        scanner.close();
    }
}

