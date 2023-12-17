

# Cryptography - SHA-256 Hashing in C#


# Introduction to Hash Functions and SHA-256

Hash functions are fundamental cryptographic algorithms used to transform input data (of any size) into a fixed-size output called a hash value or hash code. These functions play a crucial role in computer security, data integrity verification, and cryptography.

## What is a Hash Function?

A hash function takes an input (or 'message') and returns a fixed-size string of bytes. The output, known as a hash or digest, typically appears as a sequence of alphanumeric characters. Importantly, the same input always produces the same hash value.

### Characteristics of a Hash Function

- **Deterministic:** For a given input, the output hash value is always the same.
- **Fast Computation:** The hash function calculates the hash value quickly.
- **Irreversibility:** It should be computationally infeasible to reverse the process and derive the original input from the hash value.
- **Avalanche Effect:** A small change in the input drastically changes the output hash value.
- **Fixed Output Length:** The hash function produces a fixed-size output, irrespective of the input size.

## Brief Explanation of SHA-256 Code

The provided code demonstrates the usage of the SHA-256 hash function in C#. It showcases two examples:
1. **Hashing a Text String:** A predefined text string is hashed using SHA-256.
2. **Hashing a File's Content:** Reads the content of a specified file and computes its SHA-256 hash.

The code utilizes built-in C# libraries for cryptographic operations (`System.Security.Cryptography`). It defines methods to perform SHA-256 hashing for both text and byte arrays. The `CalculateSHA256` function computes the hash, while `ByteArrayToString` converts the hash output to a readable hexadecimal format.

## Code Explanation - SHA-256 Hash Function

The following C# code showcases the implementation of the SHA-256 hash function:

```csharp
using System;
using System.Security.Cryptography;
using System.Text;

class Program
{
    static void Main()
    {
        // ... (Votre code SHA-256 ici)
    }

    // SHA-256 hash function
    static byte[] CalculateSHA256(string input)
    {
        using (SHA256 sha256 = SHA256.Create())
        {
            byte[] inputBytes = Encoding.UTF8.GetBytes(input);
            return sha256.ComputeHash(inputBytes);
        }
    }

    static byte[] CalculateSHA256(byte[] inputBytes)
    {
        using (SHA256 sha256 = SHA256.Create())
        {
            return sha256.ComputeHash(inputBytes);
        }
    }

    // Convert byte array to hexadecimal string
    static string ByteArrayToString(byte[] array)
    {
        StringBuilder builder = new StringBuilder();
        foreach (byte value in array)
        {
            builder.Append(value.ToString("x2")); // Convert to hexadecimal representation


        }
        return builder.ToString();
    }
}
```
### Explanation of SHA-256 Function

#### `CalculateSHA256(string input)` Method:
This method computes the SHA-256 hash from a given input string. It first encodes the string into bytes using UTF-8 encoding and then calculates the hash using the `SHA256` class provided in the .NET Framework.

#### `CalculateSHA256(byte[] inputBytes)` Method:
This method computes the SHA-256 hash from a byte array. It's specifically designed for hashing file content represented as byte arrays. This approach allows for broader input handling, not limited to strings, enabling the hashing of file content or any data represented as bytes.

#### `ByteArrayToString(byte[] array)` Method:
This method converts the resulting byte array, which represents the hash output, into a readable hexadecimal string format. Each byte in the array is transformed into a two-character hexadecimal representation, resulting in a human-readable version of the hash.

These methods collectively provide a flexible and comprehensive approach to computing SHA-256 hashes in C#. They handle both string inputs and byte array inputs (like file contents) and ensure the output is represented in a readable format.




### Example 1: Hashing a Text String

The code snippet below demonstrates how to hash a text string using the SHA-256 function.

```csharp
// Example 1: Hashing a text string
string inputText = "This is an example of hashing in C# with SHA-256.";
byte[] hashedTextBytes = CalculateSHA256(inputText);
string hashedTextString = ByteArrayToString(hashedTextBytes);
Console.WriteLine("\n\nExample 1:");
Console.WriteLine("Input: " + inputText);
Console.WriteLine("Hashed output (SHA-256): " + hashedTextString);
Console.WriteLine();
```
#### Explanation of Example 1:
1. **Input Text:** A predefined string is used as input for the hashing process.
2. **Hash Calculation:** The `CalculateSHA256` method computes the SHA-256 hash of the input string, returning the hash as an array of bytes.
3. **Conversion to Hexadecimal:** The resulting byte array (hash) is converted into a readable hexadecimal string using the `ByteArrayToString` method.
4. **Display:** The input text along with its corresponding hashed output (in SHA-256) is printed to the console.

This example showcases the hashing process for a text string, illustrating how the input string is transformed into its corresponding SHA-256 hash.


### Example 2: Hashing the Content of a File

The code snippet below demonstrates how to hash the content of a file using the SHA-256 function.

```csharp
// Example 2: Hashing the content of a file
string filePath = "Crypto_test.txt"; // Replace with the actual file path
try
{
    byte[] fileBytes = File.ReadAllBytes(filePath);
    byte[] hashedFileBytes = CalculateSHA256(fileBytes);
    string hashedFileString = ByteArrayToString(hashedFileBytes);
    Console.WriteLine("\n\nExample 2:");
    Console.WriteLine("File path: " + filePath);
    Console.WriteLine("File hashed output (SHA-256): " + hashedFileString);
}
catch (FileNotFoundException)
{
    Console.WriteLine("\n\nExample 2:");
    Console.WriteLine("The specified file was not found.");
}
catch (Exception ex)
{
    Console.WriteLine("\n\nExample 2:");
    Console.WriteLine("An error occurred while reading the file: " + ex.Message);
}
```
#### Explanation of Example 2:
1. **File Path:** A file path pointing to the target file to be hashed is specified.
2. **Reading File Content:** The content of the specified file is read and represented as a byte array.
3. **Hash Calculation:** The `CalculateSHA256` method computes the SHA-256 hash of the file's content.
4. **Display:** The file path along with its corresponding hashed output (in SHA-256) is printed to the console.


This example illustrates how to hash the content of a file, displaying the file path and its resulting SHA-256 hash value.


### Hash function,C# Visual Studio screenshot
![image](https://github.com/leofromRTU/Crypto-rtu/assets/154064793/89bf4efe-eb4a-4322-ae96-cd56631c82bb)
![image](https://github.com/leofromRTU/Crypto-rtu/assets/154064793/1e51c2c3-3194-49a6-80df-9717e7e29c08)
![image](https://github.com/leofromRTU/Crypto-rtu/assets/154064793/9120f965-2c4c-49f1-b46d-451d980b16cf)

