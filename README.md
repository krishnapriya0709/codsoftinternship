TASK 1

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




TASK 2

import java.util.*;

public class Main2 {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
System.out.println("Enter your number of subjects:");
int n= scanner.nextInt();
float totalMarks = 0;
float avg=0;
float Markpercent=0;

System.out.println("Enter maximum marks of your exam :");
float maxscore = scanner.nextFloat();
for(int i=0;i<n;i++) {
System.out.println("Enter your marks out of " +maxscore+ " for subject " + (i + 1) + ":");
float marks = scanner.nextFloat();

totalMarks += marks;

Markpercent += marks * 100 / maxscore;
}

System.out.println("Your total marks: " + totalMarks+" out of "+n*maxscore);

avg=totalMarks/n;
System.out.println("Your average :"+avg);

Markpercent/=n;
System.out.println("Your percentage :"+Markpercent+"%");


if(Markpercent>=80){
System.out.println("O grade (OUTSTANDING)");}
else if(Markpercent>=75){
System.out.println("A grade (EXCELLENT)");}
else if(Markpercent>=70){
System.out.println("B grade (VERY GOOD)");}
else if(Markpercent>=60){
System.out.println("C grade (GOOD)");}
else if(Markpercent>=50){
System.out.println("D grade (ABOVE AVERAGE)");}
else if(Markpercent>=45){
System.out.println("E grade(AVERAGE)");}
else if(Markpercent>=40){
System.out.println("E2 grade(PASS)");}
else{
System.out.println("Fail");}
}

}


TASK 3

import java.util.Scanner;

class BankAccount {
private double balance;

public BankAccount(double balance) {
this.balance = balance;
}

public boolean deposit(double amount) {
if (amount > 0) {
balance += amount;
return true;
} else {
System.out.println("Invalid amount for deposit.");
return false;
}
}

public boolean withdraw(double amount) {
if (amount > 0 && amount <= balance) {
balance -= amount;
return true;
} else {
System.out.println("Insufficient funds or invalid amount for withdrawal.");
return false;
}
}

public double checkBalance() {
return balance;
}
}

class ATMMachine {
private BankAccount bankAccount;
private Scanner scanner;

public ATMMachine(BankAccount bankAccount) {
this.bankAccount = bankAccount;
scanner = new Scanner(System.in);
}

public void displayMenu() {
System.out.println("Welcome to the ATM");
System.out.println("1. Withdraw");
System.out.println("2. Deposit");
System.out.println("3. Check Balance");
System.out.println("4. Exit");
}

public void withdraw(double amount) {
if (bankAccount.withdraw(amount)) {
System.out.println("Withdrawal of Rs" + amount + " successful.");
} else {
System.out.println("Withdrawal failed.");
}
}

public void deposit(double amount) {
if (bankAccount.deposit(amount)) {
System.out.println("Deposit of Rs" + amount + " successful.");
} else {
System.out.println("Deposit failed.");
}
}

public void checkBalance() {
double balance = bankAccount.checkBalance();
System.out.println("Your account balance is Rs" + balance);
}

public void run() {
while (true) {
displayMenu();
System.out.print("Enter your choice: ");
String choice = scanner.nextLine();
switch (choice) {
case "1":
System.out.print("Enter the amount to withdraw: ");
double withdrawAmount = Double.parseDouble(scanner.nextLine());
withdraw(withdrawAmount);
break;
case "2":
System.out.print("Enter the amount to deposit: ");
double depositAmount = Double.parseDouble(scanner.nextLine());
deposit(depositAmount);
break;
case "3":
checkBalance();
break;
case "4":
System.out.println("Thank you for using the ATM. Goodbye!");
scanner.close();
return;
default:
System.out.println("Invalid choice. Please try again.");
}
}
}
}

public class Main {
public static void main(String[] args) {
BankAccount userAccount = new BankAccount(0); // Initialize account with balance Rs 0
ATMMachine atm = new ATMMachine(userAccount);
atm.run();
}
}
