import javax.swing.*;

public class PongBoard {
    public static void main(String[] args) {
        //running Pong
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }
        });
    }

    public static void createAndShowGUI() {
        //creating JFrame
        JFrame pongboard = new JFrame();
        pongboard.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        //adding the PongPanel
        PongPanel pong = new PongPanel();
        pongboard.add(pong);
        pongboard.setVisible(true);
        pongboard.pack();
    }
}
