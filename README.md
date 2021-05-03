# Project

import java.util.Scanner;
public class RandomNumberGuessingGame {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);

        System.out.println("Welcome to NumberGame!");

        System.out.println("Available levels of difficulty:");
        System.out.println("\t1. easy: "+"Range 1-10");
        System.out.println("\t2. normal: "+"Range 1-50");
        System.out.println("\t3. hard: "+"Range 1-500");

        System.out.print("Your choice (1-3): ");

        int difficulty = in.nextInt();

        int min;
        int max;

        if (difficulty == 1) {
             min = 1;
             max = 10;
             System.out.println("You have choosen Easy mode, Your range is from 1-10");
        } else if (difficulty == 2) {
             min = 1;
             max = 50;
             System.out.println("You have choosen Normal mode. Your range is from 1-50");
        } else {
             min = 1;
             max = 500;
             System.out.println("You have choosen Hard mode, good luck. Your range is from 1-500");
        }

        int secretNumber = getRandom(min, max);
        int numGuesses;

        if (difficulty == 1) {
             numGuesses = 4;
        } else if (difficulty == 2) {
             numGuesses = 7;
        } else {
             numGuesses = 12;
        }

        int tries = 0;
        int guess;
        do {
             System.out.printf("your guess (%d tries left): ", numGuesses - tries);
             guess = in.nextInt();
             tries++;
             if (guess == secretNumber) {
                  System.out.println("You win!");
                  if (tries == 1) {
                       System.out.println("Wow! Are you cheating?");
                  }
                  break;
             } else if (guess > secretNumber) {
                  System.out.println("Your guess is too high!");
             } else {
                  System.out.println("Your guess is too low!");
             }
        } while (tries < numGuesses);
        if (guess != secretNumber) {
             System.out.println("You lose! The secret number was " + secretNumber);
        }
    }
    public static int getRandom(int min, int max) {
        return (int)(Math.random() * (max - min + 1) + min);
    }
}
