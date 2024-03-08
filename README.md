
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
System.out.println("\nEnter your guess:");
int guess = scanner.nextInt();

if (guess == sys) {
System.out.println("Congratulations! You won :-)");
wins++;
break;
} else if (guess < sys) {
System.out.println("Your guess is too low ");
} else {
System.out.println("Your guess is too high ");
}


}

if (attempts == 3) {
System.out.println("\nSorry, you lost :-( \nThe correct number was: " + sys);
losses++;
}

System.out.println("Wins: " + wins + " Losses: " + losses);
System.out.println("\nDo you want to play again? (yes/no)");
String playChoice = scanner.next();
playAgain = playChoice.equalsIgnoreCase("yes");
}
System.out.println("Thanks for playing!");
}
}
