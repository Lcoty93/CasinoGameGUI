package com.company;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class RectangleProgramOne extends JFrame {

    public static final int WIDTH = 550;
    public static final int HEIGHT = 400;

    private JLabel rules, rules2, number, balance, betAmount, winNumber, dealerMessage;
    private JTextField numberF, balanceF, betAmountF, winNumberF, dealerF;
    private JButton betB, exitB;
    private ExitButtonHandler ebHandler;
    private BetButtonHandler betHandler;
    private int playerBalance=500;

    public RectangleProgramOne() {
        setTitle("CASINO NUMBER GUESSING GAME");

        rules = new JLabel("Guess a number between 0 and 12. ", SwingConstants.RIGHT);
        rules2 = new JLabel("Win 10 times the amount if guessed correctly!");
        balance = new JLabel("Balance: ", SwingConstants.RIGHT);
        number = new JLabel("Your Number Guess: ", SwingConstants.RIGHT);
        betAmount = new JLabel("Enter Amount To Bet: ", SwingConstants.RIGHT);
        winNumber = new JLabel("Winning Number: ", SwingConstants.RIGHT);
        dealerMessage = new JLabel("Dealer: ", SwingConstants.RIGHT);
        numberF = new JTextField(10);
        balanceF = new JTextField(10);
        betAmountF = new JTextField(10);
        winNumberF = new JTextField(10);
        dealerF = new JTextField(10);
        betB = new JButton("Bet");
        exitB = new JButton("Exit");

        Container pane = getContentPane();
        pane.setLayout(new GridLayout(7,2));


        //Exit Button
        ebHandler = new ExitButtonHandler();
        exitB.addActionListener(ebHandler);

        //Bet Button
        betHandler = new BetButtonHandler();
        betB.addActionListener(betHandler);

        pane.add(rules);
        pane.add(rules2);
        pane.add(balance);
        pane.add(balanceF);
        pane.add(number);
        pane.add(numberF);
        pane.add(betAmount);
        pane.add(betAmountF);
        pane.add(winNumber);
        pane.add(winNumberF);
        pane.add(dealerMessage);
        pane.add(dealerF);
        pane.add(exitB);
        pane.add(betB);


        setSize(WIDTH, HEIGHT);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setVisible(true);

        balanceF.setEditable(false);
        winNumberF.setEditable(false);
        dealerF.setEditable(false);

        balanceF.setText("$" + playerBalance);
        numberF.setText("(0 - 12)");
        betAmountF.setText("(0 - $500)");
    }

    private class ExitButtonHandler implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            System.exit(0);
        }
    }

    private class BetButtonHandler implements  ActionListener {
        public void actionPerformed(ActionEvent e) {
            int bettingAmount, guess, dice;

            bettingAmount = Integer.parseInt(betAmountF.getText());
            guess = Integer.parseInt(numberF.getText());

            do {
                dice = (int)(Math.random() * 13);  // generates random number 0 to 12;

                //Get players number
                if (guess < 0 || guess > 12)
                    dealerF.setText("Retry between (0 - 12)");
                else if (bettingAmount > playerBalance)
                    dealerF.setText("Betting amount greater than current balance!");
                else if (dice == guess) {
                    dealerF.setText("You are in luck!! You have won!");
                    playerBalance += bettingAmount * 10;
                    balanceF.setText("$" + playerBalance);
                }
                else {
                    dealerF.setText("Better luck next time! You lost");
                    playerBalance -= bettingAmount;
                    balanceF.setText("$" + playerBalance);
                }

                winNumberF.setText("" + dice);

            }while (playerBalance < 0);


            if (playerBalance <= 0) {
                dealerF.setText("Sorry, you have ran out of money.");
                betB.setEnabled(false);
            }

        }
    }

    public static void main(String[] args){
        new RectangleProgramOne();
    }

}
