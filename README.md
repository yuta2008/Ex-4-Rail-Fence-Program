# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM


#include <stdio.h>
#include <string.h>

int main()
{
    char text[100], rail[10][100];
    int i, j, k, len, row = 0, dir = 1, key;

    printf("Enter the plain text: ");
    scanf("%99s", text);

    printf("Enter the key (number of rails): ");
    scanf("%d", &key);

    len = strlen(text);

    if (key < 2 || key > 10)
    {
        printf("Invalid key!\n");
        return 1;
    }

    for (i = 0; i < key; i++)
        for (j = 0; j < len; j++)
            rail[i][j] = '\0';

    for (i = 0; i < len; i++)
    {
        rail[row][i] = text[i];

        if (row == 0)
            dir = 1;
        else if (row == key - 1)
            dir = -1;

        row += dir;
    }

    printf("Cipher Text: ");

    for (i = 0; i < key; i++)
        for (j = 0; j < len; j++)
            if (rail[i][j] != '\0')
                printf("%c", rail[i][j]);

    printf("\n");

    return 0;
}


# OUTPUT

<img width="342" height="201" alt="image" src="https://github.com/user-attachments/assets/07a81699-c86b-4ea1-bf3c-f511f0b5415b" />


# RESULT
Thus, the C program to implement the Rail Fence transposition technique was executed successfully, and the encrypted ciphertext was obtained.
