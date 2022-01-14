import processing.core.*;

import java.util.Random;

public class Fifteen extends PApplet {
    public static float rectX,rectY,size;
    int[][] game = new int[4][4];
    public static int emptyRaw, emptyColumn;
    int mountMoves;
    public static boolean win;

    public void settings() {
        fullScreen();
    }

    public void setup() {
        fullGame15(game);
        size = 120;
        rectX = width / 2f - 2 * size;
        rectY = height / 2f - 2 * size;
        emptyColumn = 3;
        emptyRaw = 3;
        win = false;
    }

    public void draw() {
        background(0, 0, 0);
        textSize(50);
        textAlign(CENTER, CENTER);
        fill(255, 255, 0);
        text("Game 15", width / 2f, 50);
        if (isWin(game)) {
            fill(200,155,200);
            text("You won. Your number of moves is " + mountMoves + ".Press Enter to continue",width / 2f, 800);
        } else {
            fill(255, 255, 0);
            text("Start/Restart: Enter", width / 2f, 800);
        }
        textSize(45);
        text("Moves:" + mountMoves, width / 2f + width / 3f, height / 2f);
        textSize(85);
        for (int i = 0; i < game.length; i++) {
            for (int j = 0; j < game.length; j++) {
                if (game[i][j] == 16) {
                    stroke(255, 255, 255);
                    fill(0, 0, 0);
                    rect(rectX + j * size, rectY + i * size, size, size);
                    noStroke();
                } else if (game[i][j] < 16) {
                    fill(0, 0, 255);
                    stroke(255, 255, 255);
                    rect(rectX + j * size, rectY + i * size, size, size);
                    noStroke();
                } if (game[i][j] != 16) {
                    fill(255, 255, 0);
                    text(game[i][j], rectX + j * size + size / 2f, rectY + i * size + size / 2);
                }
            }
        }
    }

    public void keyReleased() {
        if (key == ENTER) {
            dropp(game);
            win = false;
        }
        if (key == CODED) {
            switch (keyCode) {
                case UP:
                    if (emptyColumn + 1 < game.length) {
                        int t = game[emptyColumn + 1][emptyRaw];
                        game[emptyColumn + 1][emptyRaw] = 16;
                        game[emptyColumn][emptyRaw] = t;
                        emptyColumn++;
                        mountMoves++;
                    }
                    break;
                case DOWN:
                    if (emptyColumn - 1 >= 0) {
                        int t = game[emptyColumn - 1][emptyRaw];
                        game[emptyColumn - 1][emptyRaw] = 16;
                        game[emptyColumn][emptyRaw] = t;
                        emptyColumn--;
                        mountMoves++;
                    }
                    break;
                case LEFT:
                    if (emptyRaw + 1 < game.length) {
                        int t = game[emptyColumn][emptyRaw + 1];
                        game[emptyColumn][emptyRaw + 1] = 16;
                        game[emptyColumn][emptyRaw] = t;
                        emptyRaw++;
                        mountMoves++;
                    }
                    break;
                case RIGHT:
                    if (emptyRaw - 1 >= 0) {
                        int t = game[emptyColumn][emptyRaw - 1];
                        game[emptyColumn][emptyRaw - 1] = 16;
                        game[emptyColumn][emptyRaw] = t;
                        emptyRaw--;
                        mountMoves++;
                    }
                    break;
            }
        }
    }

    public static void main(String[] args) {
        PApplet.main("Fifteen");
    }

    public static void fullGame15(int[][] game) {
        int amount = 1;
        for (int i = 0; i < game.length; i++) {
            for (int j = 0; j < game[i].length; j++, amount++) {
                game[i][j] = amount;
            }
        }
    }

    public static boolean isWin(int[][] game) {
        int amount = 1;
        for (int i = 0; i < game.length; i++) {
            for (int j = 0; j < game[i].length; j++, amount++) {
                if (game[i][j] != amount) {
                    return false;
                }
            }
        }
        win = true;
        return win;
    }
    public static void dropp(int[][] game15) {
        Random random = new Random();
        for (int i = game15.length - 1; i > 0; i--) {
            for (int j = game15.length - 1; j > 0; j--) {
                int a = random.nextInt(i + 1);
                int b = random.nextInt(j + 1);

                int temp = game15[i][j];
                game15[i][j] = game15[a][b];
                game15[a][b] = temp;
            }
        }
        for (int i = 0; i < game15.length; i++) {
            for (int j = 0; j < game15[i].length; j++) {
                if (game15[i][j] == 16) {
                    emptyRaw = j;
                    emptyColumn = i;
                }
            }
        }
    }

}
