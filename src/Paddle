public class Paddle {
    private static final int STOP = 0;
    private static final int UP = 1;
    private static final int DOWN = 2;

    private int y;
    private int x;
    private int height = 100;

    public Paddle() {
        reset();
    }

    public void movePaddle(int i) {
        switch(i) {
            case STOP:
                break;
            case UP:
                if(y > 0) {
                    y -= 1;
                }
                break;
            case DOWN:
                if(y < 530) {
                    y += 1;
                }
                break;
        }
    }

    public int getY() {
        return y;
    }

    public void setX(int x) {
        this.x = x;
    }

    public int getX() {
        return x;
    }

    public int getHeight() {
        return height;
    }

    public void reset() {
        y = 250;
    }


}
