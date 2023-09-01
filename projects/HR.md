---
layout: project
type: project
image: img/HRbruh.jpg
title: "HR"
date: 2023
published: true
labels:
  - Java
  - GitHub
summary: "HR simulation that I developed for ICS 211."
---

This interactive program serves as a simulation for employees accessing their HR database.

```cpp

Hey there! This is Kapolei Target HR, Whats your name? :D
eli
Hi eli!, how can we help you?
---------------------------------------------------------
	1) Add an employee 
	2) Remove an employee 
	3) Print employees that earn more than a given amount
	4) Print all the employees 
	0) Close the program
Please choose one of the options (type 1, 2, 3, 4, 0)
---------------------------------------------------------

```

Within this program, the employee is able to add, remove, print all, or print employees who earn more than a given amount. 

Attached below is the code that runs the HR simulation:

```cpp

import java.util.*;

import java.util.Arrays;

public class HR {

   public static void main(String args[]) throws Exception {
      
      Scanner input = new Scanner(System.in);
            
      int empChecker = 0;   
      String name = ""; 
      int userChoice = 0;
      
      Employee emArr []= new Employee [5];
         
      System.out.println("Hey there! This is Kapolei Target HR, Whats your name? :D"); 
      name = input.nextLine();  
      System.out.println("Hi " + name + "!, how can we help you?");
      
      do {  
         try {
            userChoice = displayMenu(input);
         }
         catch (InputMismatchException ime) {
            System.out.println("\n***ERROR ERROR ERROR*** \nPlease enter valid values!" +
               "\n*********************** \n");
         }
         if (userChoice <= 4) {         
                 
            // User goes through a series of cases depending on what number they choose
            switch (userChoice) {
            
               case 0:        System.out.println("Have a great day, " + name + "!!!");              
                                 break;
                
               case 1:        System.out.println("***Add Employee***");          
                              emArr = addEmployee(emArr, empChecker);
                              empChecker = empChecker(emArr, empChecker);                        
                                 break;
            
               case 2:        System.out.println("***Remove Employee***");
                              remoEmployee(emArr, empChecker);                    
                                 break;
            
               case 3:        System.out.println("***Print Employees That Earn More***");
                              moreAmount(emArr, empChecker);           
                                 break;
            
               case 4:        System.out.println("***Print All Employees***");
                              emArr = printAll(emArr, empChecker); 
                                 break;
            }   
         }
         else {
         
            System.out.println("Please enter a valid number!!");
            System.out.println("EX: 1 , 2 , 3 , 4 , 0");
            
         }
      }
      
      while (userChoice != 0);   
   
   }   

   public static Employee[] addEmployee(Employee[] emArr, int empChecker) throws Exception {
      
      Scanner input = new Scanner(System.in);
      
      int empNum = 0;
      double salary = 0;
      String name = "";
     
         try {
         
            System.out.println("Please enter valid credentials"); 
            System.out.println("Employee Number: ex. 12345 (5 Numercial Values)");
            empNum = input.nextInt();
         
            System.out.println("Salary: ex. 123456 (6 or less Numercial Values)");
            salary = input.nextDouble();
         
            name = input.nextLine();
            System.out.println("Name: ex. NicoRobin (Character Values)");
            name = input.nextLine();
         
            for (Employee emp : emArr) {
               if (emp != null) {       
                  if (emp.getEnumb() == empNum) {
                  
                     System.out.println("\nSeems we already have this existing number in our datasystem...\n"); 
                  }
               }
            }
            try {
            
               
               if (empChecker == 5) {
                  System.out.println("\nITS FULL, CAN NO LONGER HOLD ANY MORE EMPLOYESS\n");
               }
               else {
                  Employee emp = new Employee(empNum, salary, name);
                  emArr[empChecker] = emp;
               }
      
            }
            catch (EmployeeException ee) {
            
               System.out.println(ee.getMessage());
            
            }   
               
         }
         catch (InputMismatchException ime) {
            System.out.println("\n***ERROR ERROR ERROR*** \nPlease enter valid values!" +
               "\n*********************** \n");    
         }
             
      return emArr;
   }
   
   public static Employee[] remoEmployee(Employee[] emArr, int empChecker) throws Exception {
      
      Scanner input = new Scanner(System.in);
      int remove = 0;
      int index = 0;
      boolean noEmp = true;
      
      for (Employee emp : emArr) {
         if (emp != null) {
            noEmp = false;
         }
      }  
      
      if (noEmp) {
         System.out.println("\nYou currently have no Employees in the database! Try entering" +
            " some first...\n");
      }
      else {
      
         System.out.println("Which Employee would you like to remove?");
         System.out.println("This is what you have in the data system so far: \n");
         
         for (int i = 0; i < emArr.length; i++) {
            if (emArr[i] != null) {
               System.out.println((i) + ". " + emArr[i].toString());
            }
            
         }
         try {
            System.out.println("Please enter the Employee number youd like to remove: ");
            remove = input.nextInt();
         }
         catch (InputMismatchException ime) {       
            System.out.println("\n***ERROR ERROR ERROR*** \nPlease enter valid values!" +
               "\n*********************** \n");
         }
         for (int i = 0; i < emArr.length; i++) {
            if(emArr[i] != null) {
               if(emArr[i].getEnumb() == remove) {
                  System.out.println("element found and deleting it...");
                  emArr[i] = null;
               }
            }  
         }
       
         for (int i = index; i < emArr.length-1; i++) {
            emArr[i] = emArr[i+1];
         }      
         
         emArr[emArr.length-1] = null;
         
      }
              
      return emArr;
   }
   
   public static Employee[] moreAmount(Employee[] emArr, int empChecker) throws Exception{
   
      Scanner input = new Scanner(System.in);
      boolean noEmp = true;
      double amt = 0;
      
      for (Employee emp : emArr) {
         if (emp != null) {
            noEmp = false;
         }
      }
      if (noEmp) {
         System.out.println("\nYou currently have no Employees in the database! Try entering" +
            " some first...\n");
      }
      else {
         try {
            System.out.println("Input the number that you would like to see: ");
            System.out.println("Be sure to enter a numerical value from $0-500000!\n");
            amt = input.nextDouble();
         }
         catch (InputMismatchException ime){
            System.out.println("\n***ERROR ERROR ERROR*** \nPlease enter valid values!" +
               "\n*********************** \n");
         }
         for (Employee emp : emArr) {
            if (emp != null) {
               if (emp.getSalary() >= amt) {
                  System.out.print("Retrieving the Employees that make over " + String.format("$%.2f",amt) + ":\n");
                  System.out.println(emp.toString());
               }
               else if (emp.getSalary() < amt) {
                  System.out.println("Im sorry, but it seems that Employee " + emp.getEnumb() + " doesnt make " + String.format("$%.2f",amt));     
               }

            }
         }
      
      }
      
      return emArr;
   }
   
   public static Employee[] printAll(Employee[] emArr, int empChecker) throws Exception {
      
      boolean noEmp = true;
      
      for (Employee employee : emArr) {
         if (employee != null) {
            noEmp = false;
         }
      }
      
      if (noEmp) {
         System.out.println("\nYou currently have no Employees in the database! Try entering" +
            " some first...\n"); 
      }
      else {
         System.out.println("\nThese are the Employee(s) you have in the database so far: \n");
         for (int i = 0; i < emArr.length; i++) {
            if (emArr[i] != null) {
               System.out.println((i) + ". " + emArr[i].toString());
            }
         }
      }
      
      return emArr;
      
   }
   
   public static int empChecker(Employee[] emArr, int empChecker) throws Exception {
      
      empChecker = 0;
      
      for (Employee employee : emArr) {
         if (employee != null) {
            empChecker++; 
         }
      }
      
      return empChecker;
   }
    
   public static int displayMenu(Scanner input) {
   
      
      System.out.println("---------------------------------------------------------");
      
      System.out.println("\t1) Add an employee \n\t2) Remove an employee \n\t3) Print employees that earn more than a given amount" +
            "\n\t4) Print all the employees \n\t0) Close the program");       
      System.out.println("Please choose one of the options (type 1, 2, 3, 4, 0)");
      
      System.out.println("---------------------------------------------------------");
         
      return input.nextInt();
   }
}

```
