import java.util.*;

public class Main {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
Random random = new Random();
boolean playAgain=true;
int wins = 0;
int losses = 0;

while (playAgain) {
int sys = random.nextInt(101);

int attempts;
for(attempts=0;attempts<3;attempts++) {
System.out.println("\nI AM IN BETWEEN 1-100 FIND ME!! :");
int guess = scanner.nextInt();

if (guess == sys) {
System.out.println("YOU FOUND ME !!!:-)");
wins++;
break;
} else if (guess < sys) {
System.out.println("OOPS!... your guess is too low");
} else {
System.out.println("OOPS!...our guess is too high ");
}


}

if (attempts == 3) {
System.out.println("\nYou couldn't find me :-( \nI am " + sys);
losses++;
}

System.out.println("Wins: " + wins + " Losses: " + losses);
System.out.println("\nDo you want to play again? (yes/no)");
String playChoice = scanner.next();
playAgain = playChoice.equalsIgnoreCase("yes");
}
System.out.println("Thanks for playing!");
}}
