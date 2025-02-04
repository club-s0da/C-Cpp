```c
//Final Exam

//For this final exam, you may use the text, your notes, and programs you have written, as well as PowerPoint slideshows used in class. 

//Scenario: You need to purchase some items at Hansen's Discount Supermarket.
//You have a list of items, but you know that when you get to the store, you will most likely purchase other things.
//After you have selected your products at the store, you get up to the self-checkout, and the scanner is broken.
//The manager approaches you because he knows that you are a knowledgeable programmer to help him quickly design a small program that will manually total items purchased and calculate the tax and final total of all sales.

//Program Specifications:
//You must use at least two different arrays:
// A character array to store the welcome message:
// An array with a float datatype to store the prices of the items. Can either leave it blank or make it a very large size.
//Prompt the user to enter how many items they have to total.
//There is a constraint:
//  If the price of any one item is greater than $10.00, it is considered invalid.
//  You must use a repetitive statement to display a message and force the user to enter a value less than $10.00.
//You need to create a function to compute the final total using a sales tax of 6% (.06).    


#include <stdio.h> // allows us to use the printf() and scanf() and puts() functions (standard input output . h)

float taxTotal(float total); // function prototype

int main() // starts the execution and termination of the program
{
    char welcome[] = "Welcome to Hansen's Discount Supermarket!"; // initialized character array to store welcome message
    float prices[] = {}; // declaration array of undeclared length, initialized, to store prices
    int items; // variable declaration
    int i; // variable declaration, serves as counter
    float grandTotal; // variable declaration
    float total = 0; // initialized variable to begin accumulating total statement

    puts(welcome); // use a puts() function to display the welcome message

    printf("How many items do you have to scan: "); //prompts user for number of items
    scanf("%d", &items); //inputs number of items into variable

    printf("\nWe are sorry, the scanner is broken at the moment.");
    printf("\nPlease enter your prices manually.\n");

    for (i = 0; i < items; i++) // for loop with range 0 to number of items-1, increment by 1
    {
        printf("\nWhat is the price of your product: ");
        scanf("%f", &prices[i]);

        if (prices[i] > 0) // if user input is greater than 0...
        {
            if (prices[i] < 10.00)  // ...AND if user input is less than 10.00
            {
            total += prices[i]; // add price at index i to accumulating total statement
            }
            else
            {
            printf("Invalid price, be sure to enter a price under $10.00\n"); // output if price is >= 10.00
            i--; // decrementer of counter to have opportunity to go back and enter a valid price if this condition is true
            }
        }
        else
        {
            printf("No freebies, please enter a valid price\n"); // output in case the user enters 0 or a negative number
            i--; // decrementer of counter to have opportunity to go back and enter a valid price if this condition is true
        }
    }

    printf("\nYour total is: %.2f", total); // display total of prices
    
    grandTotal = taxTotal(total); // function call assigned to a variable
    printf("\nYour Grand Total including Tax is: %.2f", grandTotal); // display the result of the function

    puts("\nHave a great day!"); 

    return 0;
}

// Create a function to compute the final total using a sales tax of 6% (.06)
float taxTotal(float total) // function definition to compute tax and final total
{
    float tax, finalTotal; // variable declaration
    
    tax = total * 0.06; // calculate tax
    printf("\nTax: %.2f\n", tax); // display tax
    
    finalTotal = tax + total; // calculate final total
    return finalTotal; // returns value of finalTotal when called
}

```
