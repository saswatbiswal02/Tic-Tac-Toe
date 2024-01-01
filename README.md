//# Tic-Tac-Toe
//Its the most famous game Tic-Tac-Toe. This game is developed in turbo C++ language.

#include<iostream.h>
#include<conio.h>
#include<process.h>
#include<stdlib.h>

class game {
char square[10];
int player, i, choice;
int ctr, winCountPlayer2, winCountPlayer1, drawnMatchCount;
char mark, ch;
public:
game();

void display() {
cout << "total turns played \t \t" << ctr << endl;
cout << "player 1 wins" << winCountPlayer1 << ((winCountPlayer1 <= 1)?" time":"times")<<endl;
cout << "player 2 wins" << winCountPlayer2 << ((winCountPlayer2 <=1)?" time":"times")<< endl;
cout << "Game drawn " << drawnMatchCount << ((drawnMatchCount <=1)?" time":"times")<< endl;
getch();
}

void board() {
clrscr();
cout<<"\n\n\t Tic Tac Toe \n\n";
cout<<"player 1 is X - player 2 is 0"<<endl<<endl;
cout<< endl;
cout<<"   |   | " << endl;
cout<<" " << square[1] << " | " << square[2] << " | " << square[3] << " " << endl;
cout<<"   |   | " <<endl;
cout<<"   |   | " <<endl;
cout<< " " << square[4] << " | " << square[5] << " | " << square[6] << " " << endl;
cout<<"   |   | " << endl;
cout<<"   |   | " << endl;
cout<< " " << square[7] << " | " << square[8] << " | " << square[9] << " " << endl;
cout<<"   |   | " << endl;
cout<<"   |   | " << endl;
}

void clearboard() {
board();
square[1] = '1';
square[2] = '2';
square[3] = '3';
square[4] = '4';
square[5] = '5';
square[6] = '6';
square[7] = '7';
square[8] = '8';
square[9] = '9';
}

int checkwin() {

if (square[1]==square[2] && square[2]==square[3])
return 1;
else if (square[4]==square[5] && square[5]==square[6])
return 1;
else if (square[7]==square[8] && square[8]==square[9])
return 1;
else if (square[1]==square[4] && square[4]==square[7])
return 1;
else if (square[2]==square[5] && square[5]==square[8])
return 1;
else if (square[3]==square[6] && square[6]==square[9])
return 1;
else if (square[1]==square[5] && square[5]==square[9])
return 1;
else if (square[3]==square[5] && square[5]==square[7])
return 1;
else if (square[1]!='1' && square [2]!='2' && square[3]!= '3' && square[4]!= '4' && square[5]!= '5' && square[6]!= '6' && square[7]!= '7' && square[8]!= '8' && square[9]!= '9')
return 0;
else
return -1;
}

void play();
};
void game::play() {
do {
do {
board();
game();
player = (player % 2) ? 1 : 2;
cout << "player " << player << " enter a number from 1-9: ";
cin >> choice;
while (cin.fail()) {
cout << "invalid enter numbers from 1-9" << endl;
cin.clear();
cin.ignore();
cin >> choice;
}
mark = (player - 1) ? 'X' : '0';
if (choice == 1 && square[1] == '1')
square[1] = mark;
else if (choice == 2 && square[2] == '2')
square[2] = mark;
else if (choice == 3 && square[3] == '3')
square[3] = mark;
else if (choice == 4 && square[4] == '4')
square[4] = mark;
else if (choice == 5 && square[5] == '5')
square[5] = mark;
else if (choice == 6 && square[6] == '6')
square[6] = mark;
else if (choice == 7 && square[7] == '7')
square[7] = mark;
else if (choice == 8 && square[8] == '8')
square[8] = mark;
else if (choice == 9 && square[9] == '9')
square[9] = mark;
else {
cout << "invalid move";
player--;
cin.ignore();
cin.get();
}
i = checkwin();
player++;
} while (i == -1);
if (i == 1) {
if (player % 2 == 1) {
clearboard();
cout << "==>player" << --player << " wins. Press Enter to continue \n";
winCountPlayer2++;
} else if (player % 2 == 0) {
clearboard();
cout << "==>player" << --player << " wins. Press Enter to continue \n";
winCountPlayer1++;
}
getch();
} else {
clearboard();
cout << "Game Drawn.\n";
drawnMatchCount++;
}
cout << "do you want to play again? \t press y or n \n";
cin >> ch;
if ((ch == 'y') || (ch == 'Y')) {
ctr++;
clearboard();
} else {
display();
}
cin.ignore();
} while (ch == 'y' || ch == 'Y');
}

game::game() {
square[0] = '0';
square[1] = '1'; 
square[2] = '2';
square[3] = '3';
square[4] = '4';
square[5] = '5';
square[6] = '6';
square[7] = '7';
square[8] = '8';
square[9] = '9';
player = 1;
ch = 'y';
ctr = 1;
winCountPlayer2 = 0;
winCountPlayer1 = 0;
drawnMatchCount = 0;
}

int main() {
game g1;
g1.play();
return 0;
}
