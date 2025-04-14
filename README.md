#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <math.h>

// Function to convert a hex string to a decimal number
int hex2Dec(const char* hexString) {
    int decimalValue = 0;
    int length = strlen(hexString);

    // Convert the hex string to a decimal number
    for (int i = 0; i < length; ++i) {
        char c = hexString[length - 1 - i];
        int hexDigit;

        if (isdigit(c)) {
            hexDigit = c - '0';
        } else if (isxdigit(c)) {
            hexDigit = toupper(c) - 'A' + 10;
        } else {
            printf("Error: Input is not a valid hex string.\n");
            return -1; // Return -1 in case of invalid input
        }

        decimalValue += hexDigit * (int)pow(16, i);
    }

    return decimalValue;
}

// Main function to test the hex2Dec function
int main() {
    char hexInput[100];

    printf("Enter a hex number: ");
    scanf("%99s", hexInput);

    int decimal = hex2Dec(hexInput);
    if (decimal != -1) {
        printf("The decimal value of hex \"%s\" is: %d\n", hexInput, decimal);
    }

    return 0;
}
