# Ex17 Reversing a String Using Stack Data Structure
## DATE:26.02.26
## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1. Start the program.
2. Create an empty stack of characters.
3. Traverse each character ch in the input string.
4. Create an empty StringBuilder named reversed.
5. While the stack is not empty.
6. Convert reversed to a string and return it.
7. Read the string input from the user.
8. Call and store the returned result in reversed.
9. Print the reversed string.
10. End the program.   

## Program:
```
/*
Program to reverses an input string using a stack
Developed by: VIJAY K
RegisterNumber:  212223040236
*/
```
```
import java.util.Scanner;
import java.util.Stack;

public class ReverseStringWithStack {

    public static String reverseString(String input) {
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < input.length(); i++) {
            stack.push(input.charAt(i));
        }

        StringBuilder result = new StringBuilder();

        while (!stack.isEmpty()) {
            result.append(stack.pop());
        }

        return result.toString();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();

        String reversed = reverseString(input);

        System.out.println(reversed);

        scanner.close();
    }
}
```

## Output:
<img width="381" height="285" alt="image" src="https://github.com/user-attachments/assets/14b1931b-1511-4bd7-a0ec-e06d9e95944c" />

## Result:
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.
