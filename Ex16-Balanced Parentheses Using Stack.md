# Ex16 Check for Balanced Parentheses Using Stack
## DATE:26.02.26
## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1. Start the program.
2. Stack Initialization.
3. Read the input string.
4. Create a stack st of size expr.length().
5. Repeat for each character in the string.
6. Opening Parentheses.
7.  Closing Parentheses.
8.  After Processing All Characters, if the stack is empty return true.
9.  If stack is not empty return false.
10.  Print the result.
11.  End the program. 

## Program:
```
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
Developed by: VIJAY K
RegisterNumber:  212223040236
*/
```
```
import java.util.Scanner;

class ArrayStack {
    private char[] arr;
    private int top;

    public ArrayStack(int size) {
        arr = new char[size];
        top = -1;
    }

    public void push(char c) {
        arr[++top] = c;
    }

    public char pop() {
        return arr[top--];
    }

    public boolean isEmpty() {
        return top == -1;
    }
}

public class ParenChecker {

    public static boolean isBalanced(String expr) {
        ArrayStack st = new ArrayStack(expr.length());
        for (char ch : expr.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (st.isEmpty()) return false;
                char top = st.pop();
                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }
        return st.isEmpty();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String expr = sc.nextLine();
        boolean ok = isBalanced(expr);
        System.out.println(ok);
        sc.close();
    }
}
```

## Output:
<img width="410" height="312" alt="image" src="https://github.com/user-attachments/assets/a104811b-5136-46f1-803b-c687d16e8043" />

## Result:
Thus,the program correctly checks whether an input string has balanced parentheses using a stack.
