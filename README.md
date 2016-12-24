# midproject
#include <iostream>
#include <string.h>
#include <conio.h>
#include <fstream >
#include <stdlib.h>

using namespace std;
class score
{
    private:
    char name[40];
	public:
	void getdata()
	{
		cout<<"\n\n      Enter your name : "; cin>>name ;

	}

};

char square[10] = {'o','1','2','3','4','5','6','7','8','9'};
int checkwin();
void board();
fstream f; score s;
void writedata()
{
	f.open("score.txt",ios::out|ios::app);
	s.getdata();
	f.write((char *)&s, sizeof(score ));
	f.close();
}
int main()
{
    system("color 27");
    
	int player = 1,i,choice;
	char mark;
	start:
	do
	{
		board();
		player=(player%2)?1:2;
		cout << "     Player " << player << ", enter a number:  ";
		cin >> choice;

		mark=(player == 1) ? 'X' : 'O';
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
		else
		{
			cout<<"Invalid move ";
			player--;
			getch();
		}
		i=checkwin();
		player++;
	}

	while(i==-1);
	board();
	if(i==1)
	{
		cout<<"==>\aPlayer "<<--player<<" win ";
		writedata();
	}


	else
		cout<<"==>\aGame draw";
	getch();
	cout << "Do you want to play again?\n";
	char n;
	cin >> n;
	if (n=='Y' || n=='y')
	{
		goto start;
		
	}
