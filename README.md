import java.util.Scanner;

public class DFA {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        String a;

        while (true) {
            System.out.print("Enter a binary string ( type 'exit' to quit): ");
            a = input.nextLine();

            if (a.equalsIgnoreCase("exit")) {
                System.out.println("Program ended.");
                break;
            }

            
            String state = "q0";
            boolean valid = true;

            for (int i = 0; i < a.length(); i++) {
                char symbol = a.charAt(i);

                switch (state) {
                    case "q0":
                        if (symbol == '0')
                            state = "q1";
                        else if (symbol == '1')
                            state = "q0";
                        else {
                            valid = false;
                        }
                        break;

                    case "q1":
                        if (symbol == '0')
                            state = "q1";
                        else if (symbol == '1')
                            state = "q2";
                        else {
                            valid = false;
                        }
                        break;

                    case "q2":
                        if (symbol == '0')
                            state = "q1";
                        else if (symbol == '1')
                            state = "q0";
                        else {
                            valid = false;
                        }
                        break;
                }

                if (!valid) break;
            }

            if (!valid) {
                System.out.println("Invalid input! Only 0 and 1 are allowed.");
            } else if (state.equals("q2")) {
                System.out.println("Output: Accepted\n");
            } else {
                System.out.println("Output: Rejected\n");
            }
        }
    }
}
