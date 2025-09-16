# Caesar-cipher--Java-code
##Caesar cipher is one of the simplest and earliest encryption techniques, where each letter in the plaintext is shifted by a fixed number of positions in the alphabet. For example, with a shift of 3, A becomes D, B becomes E, and so on. Though easy to understand and implement, it is highly insecure and can be broken using simple frequency analysis.

import java.util.*;

public class ceaser{

	 static int key = 3;
	 public static String encrypt(String msg) {
	 String enc = "";
	 for (int i = 0; i < msg.length(); i++) {
	 char ch = msg.charAt(i);
	 if (ch >= 'A' && ch <= 'Z') {
	 enc += (char) ((ch + key- 'A') % 26 + 'A');
	 } else if (ch >= 'a' && ch <= 'z') {
	 enc += (char) ((ch + key- 'a') % 26 + 'a');
	 } else {
	 enc += ch;
	 }
	 }
	 System.out.println("Encrypted Text: " + enc);
	 return enc;
	 }
	 public static void decrypt(String msg) {
	 String dec = "";
	 for (int i = 0; i < msg.length(); i++) {
	 char ch = msg.charAt(i);
	 if (ch >= 'a' && ch <= 'z') {
	 dec += (char) ((ch- key- 'a' + 26) % 26 + 'a');
	 } else if (ch >= 'A' && ch <= 'Z') {
	 dec += (char) ((ch- key- 'A' + 26) % 26 + 'A');
	 } else {
	 dec += ch;
	 }
	 }
	 System.out.println("Decrypted Text: " + dec);
	 }
	 public static void main(String[] args) {
	 Scanner sc = new Scanner(System.in);
	 String str;
	 System.out.print("Enter message: ");
	 str = sc.nextLine();
	 String enc = encrypt(str);
	 decrypt(enc);
	 }
	 }

