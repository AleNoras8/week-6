#include <iostream>
#include <string>
#include <stdexcept>
#include <cctype>
#include <cmath>

// Function to convert a hex string to a decimal number
int hex2Dec(const std::string& hexString) {
    // Check if the string is a valid hex number
    for (char c : hexString) {
        if (!std::isxdigit(c)) {  // Check if each character is a valid hex digit
            throw std::invalid_argument("Input is not a valid hex string.");
        }
    }

    int decimalValue = 0;
    int length = hexString.length();
    
    // Convert the hex string to a decimal number
    for (int i = 0; i < length; ++i) {
        char c = hexString[length - 1 - i];
        int hexDigit = (std::isdigit(c)) ? c - '0' : std::toupper(c) - 'A' + 10;
        decimalValue += hexDigit * static_cast<int>(std::pow(16, i));
    }

    return decimalValue;
}

// Main function to test the hex2Dec function
int main() {
    std::string hexInput;

    std::cout << "Enter a hex number: ";
    std::cin >> hexInput;

    try {
        int decimal = hex2Dec(hexInput);
        std::cout << "The decimal value of hex \"" << hexInput << "\" is: " << decimal << std::endl;
    } catch (const std::invalid_argument& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }

    return 0;
}
