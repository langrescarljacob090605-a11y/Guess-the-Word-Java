import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class GuessingWord {
    public GuessingWord() {
        String filename = "word.txt";
        Path path = Paths.get(filename);
        String[] temparr = new String[100];
        String[] newarr;
        Random rnd = new Random();
        Scanner scn = new Scanner(System.in);
        String hideword;
        String displayword;

        int counter = 0;

        try {
            InputStream input = Files.newInputStream(path);
            BufferedReader reader = new BufferedReader(new InputStreamReader(input));

            String word;

            while ((word = reader.readLine()) != null) {
                temparr[counter] = word;
                ++counter;
            }

            newarr = Arrays.copyOf(temparr, counter);

            hideword = newarr[rnd.nextInt(counter)];
            displayword = hideword.replaceAll("[a-zA-Z]", "?");

            boolean isTrue = true;
            boolean found;

            System.out.println("Welcome to Guessing Game!");

            do {
                System.out.println("\n\n" + displayword + "\n\n");

                System.out.print("Enter a letter or guess the word: ");
                String guess = scn.nextLine();

                if (guess.length() > 1) {
                    if (guess.equalsIgnoreCase(hideword)) {
                        System.out.print("Congrats you guessed the WORD!!");
                        System.exit(0);
                    } else {
                        System.out.println("Nice try!!");
                    }
                } else {
                    found = false;
                    for (int x = 0; x < hideword.length(); x++) {
                        if (guess.equalsIgnoreCase(String.valueOf(hideword.charAt(x)))) {
                            displayword = displayword.substring(0, x) + guess + displayword.substring(x + 1);
                            found = true;
                        }
                    }

                    if (found) {
                        System.out.println(guess.toUpperCase() + " letter is found! ");
                    } else {
                        System.out.println(guess.toUpperCase() + " letter is unknown! ");
                    }
                }

            } while (isTrue);

            System.out.println(displayword);

        } catch (IOException ex) {
            ex.printStackTrace();
        }
    }

    public static void main(String[] args) {
        new GuessingWord();
    }
}
