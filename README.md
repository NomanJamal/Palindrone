# Palindrone
This is Level 1 Task 2
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class PalindromeCheckerGUI {
    public static void main(String[] args) {
        // JFrame 
        JFrame frame = new JFrame("Palindrome Checker");
        frame.setSize(400, 250);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);
        frame.getContentPane().setBackground(new Color(245, 245, 245));

        // Label
        JLabel label = new JLabel("Enter a word or phrase:");
        label.setBounds(30, 30, 300, 25);
        label.setFont(new Font("Arial", Font.PLAIN, 14));
        frame.add(label);

        // TextField
        JTextField inputField = new JTextField();
        inputField.setBounds(30, 60, 320, 30);
        inputField.setFont(new Font("Arial", Font.PLAIN, 14));
        frame.add(inputField);

        // Button
        JButton checkButton = new JButton("Check");
        checkButton.setBounds(140, 100, 100, 30);
        checkButton.setBackground(new Color(100, 149, 237));
        checkButton.setForeground(Color.WHITE);
        frame.add(checkButton);

        // Result Label
        JLabel resultLabel = new JLabel("");
        resultLabel.setBounds(30, 150, 320, 30);
        resultLabel.setFont(new Font("Arial", Font.BOLD, 14));
        resultLabel.setHorizontalAlignment(SwingConstants.CENTER);
        frame.add(resultLabel);

        // Button Click Event
        checkButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String input = inputField.getText();

                // Input clear
                String cleaned = input.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();

                // Palindrome check
                int left = 0, right = cleaned.length() - 1;
                boolean isPalindrome = true;

                while (left < right) {
                    if (cleaned.charAt(left) != cleaned.charAt(right)) {
                        isPalindrome = false;
                        break;
                    }
                    left++;
                    right--;
                }

                // Result दिखाना
                if (input.isEmpty()) {
                    resultLabel.setForeground(Color.RED);
                    resultLabel.setText("Please enter something!");
                } else if (isPalindrome) {
                    resultLabel.setForeground(new Color(34, 139, 34)); // Green
                    resultLabel.setText(" It's a Palindrome!");
                } else {
                    resultLabel.setForeground(Color.RED);
                    resultLabel.setText("Not a Palindrome!");
                }
            }
        });

        frame.setVisible(true);
    }
}
