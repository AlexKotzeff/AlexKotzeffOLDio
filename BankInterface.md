[Back](JavaProjects.md)

package com.company;

import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        BankAccount obj1 = new BankAccount("XYZ", "123");
        obj1.showMenu();
    }
}

class BankAccount{
    int balance;
    int previousTransaction;
    String customerName;
    String customerId;

    BankAccount(String customerName, String customerId){
        this.customerName = customerName;
        this.customerId = customerId;
    }

    void deposit(int amount){
        if (amount != 0){
            balance = balance + amount;
            previousTransaction = amount;
        }
    }

    void withdraw(int amount){
        if(amount != 0){
            balance = balance - amount;
            previousTransaction = -amount;
        }
    }

    void getPreviousTransaction(){
        if(previousTransaction > 0 ){
            System.out.println("Deposited: " + previousTransaction);
        }
        else if (previousTransaction < 0){
            System.out.println("Withdrawn: " + Math.abs(previousTransaction));
        }
        else{
            System.out.println("No transaction");
        }
    }

    void showMenu(){
        String selection;
        Scanner kb = new Scanner(System.in);

        System.out.println("Welcome " + customerName);
        System.out.println("Your ID is " + customerId);
        System.out.println("\n");
        System.out.println("A. Check Balance");
        System.out.println("B. Deposit");
        System.out.println("C. Withdraw");
        System.out.println("D. Previous Transaction");
        System.out.println("E. Exit");

        do{
            System.out.println("======================================================================");
            System.out.println("Enter an option");
            System.out.println("======================================================================");
            selection = kb.next();
            System.out.println("\n");

            switch(selection) {
                case ("A"):
                    System.out.println("--------------------------------------------------------------------");
                    System.out.println("Balance = " + balance);
                    System.out.println("--------------------------------------------------------------------");
                    System.out.println("\n");
                case ("B"):
                    System.out.println("--------------------------------------------------------------------");
                    System.out.println("Enter an amount to deposit");
                    System.out.println("--------------------------------------------------------------------");
                    int amount = kb.nextInt();
                    deposit(amount);
                    System.out.println("\n");
                case ("C"):
                    System.out.println("--------------------------------------------------------------------");
                    System.out.println("Enter an amount to withdraw");
                    System.out.println("--------------------------------------------------------------------");
                    int amountToWithdraw = kb.nextInt();
                    withdraw(amountToWithdraw);
                    System.out.println("\n");
                case ("D"):
                    System.out.println("--------------------------------------------------------------------");
                    getPreviousTransaction();
                    System.out.println("--------------------------------------------------------------------");
                    System.out.println("\n");
                default:
                    System.out.println("Invalid option please try again.");
            }
            }while(!selection.equals("E"));
            System.out.println("Thank you for using our services.");
    }
}
