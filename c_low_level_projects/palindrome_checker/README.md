# The Palindrome Checker

This is a program written in C that checks whether a given word or phrase is a palindrome or not.

#include <stdio.h>

#include <string.h>

* These lines include the standard input/output library and string manipulation library for the program.

#define MAX_LENGTH 100

* This line defines a constant MAX_LENGTH with a value of 100. This constant will be used later to set the maximum length of the input string.

int check_palindrome(char *str)
{
    int i, j;

    for (i = 0, j = strlen(str) - 1; i < j; i++, j--)
    {
        if (str[i] != str[j])
        {
            return 0;
        }
    }

    return 1;
}

* This is a function called check_palindrome that takes a string as an argument and checks if it is a palindrome. The function iterates over the string from the beginning and the end, comparing the characters at each position until the middle is reached. If any pair of characters doesn't match, the function returns 0 to indicate that the string is not a palindrome. If the function completes the iteration without finding any non-matching pairs, it returns 1 to indicate that the string is a palindrome.

int main(void)
{
    char input[MAX_LENGTH];
    char choice = 'y';

    while (choice == 'y' || choice == 'Y')
    {
        printf("Enter a word or phrase: ");
        fgets(input, MAX_LENGTH, stdin);

        /* Remove newline character from input string*/
        input[strcspn(input, "\n")] = '\0';

        /* Check if input is a palindrome*/
        if (check_palindrome(input))
        {
            printf("'%s' is a palindrome.\n", input);
        }
        else
        {
            printf("'%s' is not a palindrome.\n", input);
        }

        printf("Do you want to check another word or phrase? (y/n): ");
        scanf(" %c", &choice);
        getchar(); /* Consume newline character from input buffer*/
    }

    printf("Goodbye!\n");
    return 0;
}

* This is the main function of the program, which serves as its entry point. The function declares a character array called input with a size of MAX_LENGTH to hold the user's input and a character variable choice to hold the user's choice to check another word or phrase.

* The while loop allows the user to check multiple words or phrases until they choose to exit. The printf function asks the user to enter a word or phrase, and the fgets function reads the input from the standard input stream into the input array. The strcspn function removes the newline character from the input string.

* The program then calls the check_palindrome function to determine whether the input string is a palindrome. If it is, the program prints a message indicating that the input string is a palindrome. If not, it prints a message indicating that it is not.

* The program then asks the user if they want to check another word or phrase, and reads their response using the scanf function. Finally, the program uses the getchar function to consume the newline character in the input buffer, to avoid issues with the next fgets call.

* If the user chooses not to check another word or phrase, the program prints a goodbye message and returns 0.

