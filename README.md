# EX14 - Implement-Hash-Function
## AIM :
To generate a simple hash of a given message using a custom hash function.

## DESIGN STEPS :
### Step 1 : 
Input a message from the user.

### Step 2 : 
Use a basic custom hash function that applies simple operations like XOR and addition on the characters of the message.

### Step 3 : 
Convert the resulting hash into a hexadecimal format.

### Step 4 : 
Display the computed hash to the user.

### Step 5 :
Optionally verify the hash by recomputing it and comparing it with a received hash.

## PROGRAM :
```
#include <stdio.h>
#include <string.h>

// Function to compute a simple hash of the message
void computeSimpleHash(const char *message, unsigned char *hash) {
    unsigned char temp = 0; // Temporary variable to store hash value

    // Iterate through each character in the message
    for (int i = 0; message[i] != '\0'; i++) {
        temp ^= message[i]; // XOR operation
        temp += message[i];  // Add the character value
    }
    
    *hash = temp; // Store the computed hash
}

// Function to read the received hash from user input
unsigned int readReceivedHash() {
    char receivedHash[3]; // Buffer for input (2 hex digits + null terminator)
    printf("Enter the received hash (in hex): ");
    scanf("%2s", receivedHash); // Read up to 2 characters

    unsigned int receivedHashValue;
    sscanf(receivedHash, "%02x", &receivedHashValue); // Convert hex string to integer
    return receivedHashValue; // Return the converted value
}

// Main function to execute the hash computation and verification process
int main() {
    char message[256];          // Buffer for the input message
    unsigned char hash;         // Variable to store computed hash

    // Step 1: Input the message
    printf("Enter the message: ");
    scanf("%255s", message); // Read up to 255 characters to prevent overflow

    // Step 2: Compute the hash of the message
    computeSimpleHash(message, &hash);

    // Step 3: Display the computed hash in hexadecimal format
    printf("Computed Hash (in hex): %02x\n", hash);

    // Step 4: Read and verify the received hash
    unsigned int receivedHashValue = readReceivedHash();
    
    // Step 5: Compare computed hash with received hash
    if (hash == receivedHashValue) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0; // Indicate that the program finished successfully
}

```

## OUTPUT :

![image](https://github.com/user-attachments/assets/dac6abb9-5bf3-41bc-af4a-9869a33c71b1)

## RESULT :
The program for generating and verifying a simple hash of a given message using a custom hash function was executed successfully. The computed hash ensures basic integrity of the message.
