# Caesar-cipher--Java-code
##Caesar cipher is one of the simplest and earliest encryption techniques, where each letter in the plaintext is shifted by a fixed number of positions in the alphabet. For example, with a shift of 3, A becomes D, B becomes E, and so on. Though easy to understand and implement, it is highly insecure and can be broken using simple frequency analysis.
##Code line by line explaination
Code Walkthrough
import java.util.*;
Imports all classes from the java.util package.
This is needed for Scanner, which is used for taking user input.

public class ceaser {
Defines a public class named ceaser.
(Note: Java convention suggests class names should start with a capital letter, e.g., Caesar.)

static int key = 3;
Declares a static integer variable key with value 3.
This is the shift value for the Caesar cipher (each letter is shifted forward or backward by 3).

##Encryption Method
public static String encrypt(String msg) {
Defines a static method encrypt that takes a String msg and returns an encrypted string.

String enc = "";
Creates an empty string enc to store the encrypted result.

for (int i = 0; i < msg.length(); i++) {
Loops through each character of the input string msg.

char ch = msg.charAt(i);
Extracts the character at position i.

if (ch >= 'A' && ch <= 'Z') {
    enc += (char) ((ch + key - 'A') % 26 + 'A');
}
If the character is uppercase:
Convert it into a 0–25 range by subtracting 'A'.
Add the shift (key).
Apply % 26 to wrap around if it goes past 'Z'.
Convert back to an uppercase letter by adding 'A'.
Append the encrypted character to enc.

else if (ch >= 'a' && ch <= 'z') {
    enc += (char) ((ch + key - 'a') % 26 + 'a');
}
If the character is lowercase:
Same logic as uppercase, but relative to 'a'.

else {
    enc += ch;
}
If the character is not a letter (e.g., space, digit, punctuation), leave it unchanged.

System.out.println("Encrypted Text: " + enc);
return enc;
Prints the encrypted text.
Returns it so it can be used later in decryption.

##Decryption Method
public static void decrypt(String msg) {
Defines a static method decrypt that takes the encrypted string.

String dec = "";
Creates an empty string dec to store the decrypted result.

for (int i = 0; i < msg.length(); i++) {
    char ch = msg.charAt(i);
Loops through each character of the encrypted message.
if (ch >= 'a' && ch <= 'z') {
    dec += (char) ((ch - key - 'a' + 26) % 26 + 'a');
}

If the character is lowercase:
Subtract key instead of adding it (to shift back).
Add 26 before % 26 to avoid negative results.
Convert back to a character and append to dec.

else if (ch >= 'A' && ch <= 'Z') {
    dec += (char) ((ch - key - 'A' + 26) % 26 + 'A');
}
If the character is uppercase:
Same logic as lowercase but relative to 'A'.

else {
    dec += ch;
}
Non-alphabet characters remain unchanged.
System.out.println("Decrypted Text: " + dec);
Prints the decrypted text (original message).

##Main Method
public static void main(String[] args) {
The entry point of the program.

Scanner sc = new Scanner(System.in);
String str;
System.out.print("Enter message: ");
str = sc.nextLine();
Creates a Scanner object for reading input.
Prompts the user for a message.
Reads the full input line into str.

String enc = encrypt(str);
decrypt(enc);
Encrypts the user input using the encrypt method.
Passes the encrypted string to the decrypt method to get back the original.

}
}


Closes the main method and class definition.
