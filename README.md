# Battlefeild-Boardgame
/* Kisona Richards
1st program
Any questions email me
*/

import java.util.Scanner;
public class Battleship{
    public static void main(String[] args){
        Scanner data = new Scanner(System.in);
        String guess= " ";
        int totalships = 9;

        char guessBoard [][] = { //used to find length of array
                {' ', '1', '2', '3', '4', '5', '6'},

                {'A', '-', '-', '-', '-', '-', '-'},

                {'B','-', '-', '-', '-', '-', '-'},

                {'C','-', '-', '-', '-', '-', '-'},

                {'D','-', '-', '-', '-', '-' ,'-'},

                {'E','-', '-', '-', '-', '-', '-'},

                {'F','-', '-', '-', '-', '-', '-'}}; 

        do{
            System.out.println("Please enter a guess in the form 'B5':");// prompts user
            guess = data.nextLine(); //accepts data

            int guessCol =  Integer.parseInt(guess.substring(1));
            int guessRow = chartointconverter( guess.substring(0,1));

            if(guess.toUpperCase().equals("A1")||guess.toUpperCase().equals("B1") ||guess.toUpperCase().equals("F3") || guess.toUpperCase().equals("F4") || guess.toUpperCase().equals ("F5") || guess.toUpperCase().equals ("F6") ||guess.toUpperCase().equals("B5") || guess.toUpperCase().equals("C5") || guess.toUpperCase().equals("D5")){
                System.out.print(" "+"is a hit");
                shipsunken(guess);// function to tell which ship has sunken
                totalships --; //decrements to tell how many more times the game should run
                guessBoard[guessRow][guessCol] = 'X';
               System.out.println();
                for (int row = 0; row < guessBoard.length; row++) {
                for (int col = 0; col < guessBoard.length; col++) {// prints the boards at and places X where required
                    System.out.print (guessBoard[row][col]+ "  ");//prints each row
                }
                System.out.println();// Starts a new row at the end of each row 
            }

            }else{
                guessBoard[guessRow ][guessCol] = 'O';
                System.out.print(" is a miss");
                System.out.println();
                for (int row = 0; row < guessBoard.length; row++) {// prints the boards at and places O where required
                for (int col = 0; col < guessBoard.length; col++) {
                    System.out.print (guessBoard[row][col]+ "  ");//prints each row
                }
                System.out.println();// Starts a new row at the end of each row 
            }

            }
            
            
        }while(totalships !=0);// condition to end loop and game
        
        System.out.println ("Game over, You Win!");
        
        for (int row = 0; row < guessBoard.length; row++) {// prints the boards at the end of the game
                for (int col = 0; col < guessBoard.length; col++) {
                    System.out.print (guessBoard[row][col]+ "  ");//prints each row
                }
                System.out.println();// Starts a new row at the end of each row 
            }

    }

    private static int chartointconverter(String row){ // method to convert char to int datatype
        int x = 0;
        if( row.toUpperCase().equals( "A" )){
            x=1;
        }else if(  row.toUpperCase().equals( "B" )){
            x=2;
        }else if(  row.toUpperCase().equals( "C" )){
            x=3;
        }else if(  row.toUpperCase().equals( "D" )){
            x=4;
        }else if(  row.toUpperCase().equals( "E" )){
            x=5;
        }else if(  row.toUpperCase().equals( "F" )){
            x=6;       
        } 
        return x;
    }

    public static String shipsunken(String ans){    // method to check if a ship has sunken
            int patrolBoat=2;
            int Destroyer =3;
            int Battleship = 4;
            String x="";
            
        if (ans =="A1" && ans =="B1") {
            patrolBoat--;
            if (patrolBoat == 0){
                x= "You sunk the Patrol Boat!";
                System.out.println(x);
            }
        } else if (ans ==("B5") && ans ==("C5") && ans ==("D5")) {
            Destroyer--;
            if (Destroyer == 0){
                x="You sunk the Destroyer!";
                System.out.println(x);
            }
        } else if (ans ==("F3") && ans == ("F4") && ans == ("F5") &&ans == ("F6")) {
            Battleship--;
            if (Battleship == 0){
               x="You sunk the Battleship!";
               System.out.println(x);
            }
        }
        return x;
        }
        }
        

