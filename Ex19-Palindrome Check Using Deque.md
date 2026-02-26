# Ex19 Palindrome Check Using Deque
## DATE:26.02.26
## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.

## Algorithm
1. Start the program.
2. Read the input string message.
3. Convert the string to lowercase.
4. Remove all non-alphanumeric characters using a regular expression.
5. Create an empty Deque (double-ended queue).
6. For each character c in the cleaned string.
7. While the deque contains more than one character.
8. If all pairs matched (or string has 0/1 character), return true.
9. If return value is true → print "Palindrome" , Otherwise → print "Not a palindrome".
10. End the program.      

## Program:
```
/*
Program to checks whether a given message is a palindrome by removing all non-alphanumeric characters.
Developed by: VIJAY K
RegisterNumber:  212223040236
*/
```
```
import java.util.*;

public class PalindromeChecker {
    
    public static boolean isPalindrome(String message) {
        StringBuilder cleaned = new StringBuilder();

        for (int i = 0; i < message.length(); i++) {
            char c = message.charAt(i);
            if (Character.isLetterOrDigit(c)) {
                cleaned.append(Character.toLowerCase(c));
            }
        }

        Deque<Character> deque = new ArrayDeque<>();

        for (int i = 0; i < cleaned.length(); i++) {
            deque.addLast(cleaned.charAt(i));
        }

        while (deque.size() > 1) {
            if (!deque.removeFirst().equals(deque.removeLast())) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String input = scanner.nextLine();

        if (isPalindrome(input)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not a palindrome");
        }

        scanner.close();
    }
}
```

## Output:
<img width="433" height="282" alt="image" src="https://github.com/user-attachments/assets/4242dec0-5998-46ba-8123-f33ddbf742d6" />

## Result:
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.
