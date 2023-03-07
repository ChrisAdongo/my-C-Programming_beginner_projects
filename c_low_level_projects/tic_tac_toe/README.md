# The Tic Tac Toe Game!

The program should allow two players to take turns marking X's and O's on a 3x3 grid, and should determine a winner or a tie.

#include <stdio.h>

#include <stdbool.h>

* This includes the standard input-output header file and the boolean header file.

void display_board(char board[3][3]) {

* This defines the display_board() function that takes a 2D array of characters (i.e., the board) as input.

printf("\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf(" %c ", board[i][j]);
            if (j < 2) {
                printf("|");
            }
        }
        printf("\n");
        if (i < 2) {
            printf("-----------\n");
        }
    }
    printf("\n");

* This function displays the current state of the board on the screen using a loop to iterate over each row and column of the board array. It also adds some formatting to make the output more visually appealing.

bool check_winner(char board[3][3], char mark) {

* This defines the check_winner() function that takes the board array and a mark (X or O) as input.

for (int i = 0; i < 3; i++) {
        if (board[i][0] == mark && board[i][1] == mark && board[i][2] == mark) {
            return true;
        }
        if (board[0][i] == mark && board[1][i] == mark && board[2][i] == mark) {
            return true;
        }
    }
    if (board[0][0] == mark && board[1][1] == mark && board[2][2] == mark) {
        return true;
    }
    if (board[0][2] == mark && board[1][1] == mark && board[2][0] == mark) {
        return true;
    }
    return false;

* This function checks if there is a winner by iterating over all the rows, columns, and diagonals of the board and checking if all three cells contain the same mark. If there is a winner, it returns true; otherwise, it returns false.

bool check_tie(char board[3][3]) {

* This defines the check_tie() function that takes the board array as input.

for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i][j] == ' ') {
                return false;
            }
        }
    }
    return true;

* This function checks if there is a tie by iterating over all the cells of the board and checking if any cell is empty. If there is an empty cell, it returns false; otherwise, it returns true.

int main() {
    char board[3][3] = { {' ', ' ', ' '}, {' ', ' ', ' '}, {' ', ' ', ' '} };
    char current_player = 'X';
    int row, col;

    printf("Welcome to Tic Tac Toe!\n");
    printf("Player 1: X, Player 2: O\n");
    display_board(board);

* This is the main function that initializes the board array to empty spaces, sets the current player to X, and prompts the players to enter their row and column choices. It also displays the initial state of the board on the screen using the display_board() function.
