import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class PongPanel extends JPanel implements Runnable {
    private static final int DIMX = 952;
    private static final int DIMY = 630;

    private static final int STOP = 0;
    private static final int UP = 1;
    private static final int DOWN = 2;

    private boolean running = false;

    private boolean moving1 = false;
    private boolean moving2 = false;
    private int move1 = STOP;
    private int move2 = STOP;

    private int fps = 25;

    Paddle pad1 = new Paddle();
    Paddle pad2 = new Paddle();
    Ball ball = new Ball();

    public PongPanel() {
        setPreferredSize(new Dimension(DIMX, DIMY));

        setBackground(Color.BLACK);
        setOpaque(true);
        setFocusable(true);

        pad1.setX(10);
        pad2.setX(926);

        Thread th = new Thread(this);
        th.start();

        addKeyListener(new KeyListener() {
            @Override
            public void keyTyped(KeyEvent e) {

            }

            @Override
            public void keyPressed(KeyEvent e) {
                if(e.getKeyCode() == KeyEvent.VK_UP) {
                    moving2 = true;
                    move2 = UP;
                }
                else if(e.getKeyCode() == KeyEvent.VK_DOWN) {
                    moving2 = true;
                    move2 = DOWN;
                }
                if(e.getKeyCode() == KeyEvent.VK_W) {
                    moving1 = true;
                    move1 = UP;
                }
                if(e.getKeyCode() == KeyEvent.VK_S) {
                    moving1 = true;
                    move1 = DOWN;
                }
            }

            @Override
            public void keyReleased(KeyEvent e) {
                if(e.getKeyCode() == KeyEvent.VK_UP || e.getKeyCode() == KeyEvent.VK_DOWN) {
                    moving2 = false;
                    move2 = STOP;
                }
                else if(e.getKeyCode() == KeyEvent.VK_W || e.getKeyCode() == KeyEvent.VK_S) {
                    moving1 = false;
                    move1 = STOP;
                }
            }
        });
    }

    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.setColor(Color.WHITE);
        g.fillRect(pad1.getX(), pad1.getY(), 16, pad1.getHeight());
        g.fillRect(pad2.getX(), pad2.getY(), 16, pad2.getHeight());
        g.fillOval(ball.getX(), ball.getY(), ball.getDIM(), ball.getDIM());
        g.setFont(new Font("Monospaced", Font.BOLD, 50));
        g.drawString("" + ball.getScore1(), 406, 50);
        g.drawString("" + ball.getScore2(), 500, 50);
    }

    public void run() {
        running = true;
        int tf = 0;

        while(running) {
            long starttime = System.nanoTime();
            update();
            repaint();

            try {
                Thread.sleep(3);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

            //printing the fps in the console bc i didnt want to put it in the game
            //every 69 frames calculates fps
            if(tf == 0) {
                fps = (int) (100000000 / (System.nanoTime() - starttime));
                System.out.print("\rFPS: " + fps);
                tf++;
            } else if(tf == 69) {
                tf = 0;
            } else {
                tf++;
            }
        }
    }

    private void update() {
        if(moving1) {
            pad1.movePaddle(move1);
        }
        if(moving2) {
            pad2.movePaddle(move2);
        }

        ball.move();
        ball.collision(pad1.getY(), pad2.getY());
    }
}
