```cpp
// Football tournament simualation
#include <bits/stdc++.h>
#include <fstream>
using namespace std;
class Teams
{
public:
    string team_name;
    int team_score;

    void getname()
    {
        cin >> team_name;
    }
    void getscore()
    {
        cin >> team_score;
        return;
    }
    operator string()
    {
        return team_name;
    }
};

class match : public Teams
{
public:
    int team_score1;
    int team_score2;
    virtual int matches(int i, Teams &t1, Teams &t2) = 0;
    virtual void showmatches(Teams t1, Teams t2)
    {
        cout << "this is the match";
    }
};

class Quarterfinal : public match
{
protected:
    int l = 1;
    int k = 1;

public:
    void showmatches(Teams t1, Teams t2)
    {
        cout << "                            Quarterfinal " << l << " will be played between ";
        cout << t1.team_name << " v/s " << t2.team_name << endl;
        l++;
    }
    int matches(int i, Teams &t1, Teams &t2)
    {
        cout << "\n";
        cout << "                            Quarterfinal " << k << " starts" << endl;
        cout << "                                Enter the no. of goals scored by " << t1.team_name << endl;
        t1.getscore();
        cout << "                               Enter the no. of goals scored by " << t2.team_name << endl;
        t2.getscore();
        if (t1.team_score > t2.team_score)
        {
            cout << "                         " << t1.team_name
                 << " has won Quarterfinal " << k << endl;
            k++;
            return i;
        }
        else if (t1.team_score == t2.team_score)
        {
            cout << "                        "
                 << "Quarterfinal " << k << " is draw " << endl;
            cout << "                         Now to make one team winner(knockout tournament) we can increase the score of one team by 1" << endl;
            cout << "                         press any int number except 0 to increase score of team " << t1.team_name << endl;
            cout << "                         press 0 to increase score of team " << t2.team_name << endl;
            int w;
            cin >> w;
            if (w)
            {
                cout << "                     " << t1.team_name
                     << " has won Quarterfinal " << k << endl;
                     t1.team_score++;
                k++;
                return i;
            }
            else
            {

                cout << "                     " << t2.team_name
                     << " has won Quarterfinal " << k << endl;
                   t2.team_score++;  
                k++;
                return i + 1;
            }
        }
        else
        {
            cout << "                         " << t2.team_name << " has won Quarterfinal " << k << endl;
            k++;
            return i + 1;
        }
    }
};

class Semifinals : public match
{
protected:
    int k = 1;
    int l = 1;

public:
    void showmatches(Teams t1, Teams t2)
    {
        cout << "                            Semifinal " << l << "  will be played between   ";
        cout << t1.team_name << " v/s " << t2.team_name << endl;
        l++;
    }
    int matches(int i, Teams &t1, Teams &t2)
    {
        cout << endl;
        cout << "                            Semifinal " << k << " starts   " << endl;
        cout << "                                Enter the no. of goals scored by " << t1.team_name << endl
             << endl;
        t1.getscore();
        cout << "                               Enter the no. of goals scored by " << t2.team_name << endl
             << endl;
        t2.getscore();
        if (t1.team_score > t2.team_score)
        {
            cout << "                         " << t1.team_name << " has won Semifinal " << k << endl;
            k++;
            return i;
        }
        else if (t1.team_score == t2.team_score)
        {
            cout << "                        "
                 << " Semifinal " << k << " is draw " << endl;
            cout << "                         Now to make one team winner(knockout tournament) we can increase the score of one team by 1" << endl;
            cout << "                         press any int number except 0 to increase score of team " << t1.team_name << endl;
            cout << "                         press 0 to increase score of team " << t2.team_name << endl;
            int w;
            cin >> w;
            if (w)
            {
                cout << "                     " << t1.team_name << " has won  Semifinal " << k << endl;
                k++;
                return i;
            }
            else
            {
                cout << "                     " << t2.team_name << " has won Semifinal " << k << endl;
                k++;
                return i + 1;
            }
        }
        else
        {
            cout << "                         " << t2.team_name << " has won  Semifinal  " << k << endl;
            k++;
            return i + 1;
        }
    }
};

class Final : public match
{
public:
    void showmatches(Teams t1, Teams t2)
    {
        cout << "                                 final will be played between   ";
        cout << t1.team_name << " "
             << "v/s"
             << " " << t2.team_name << endl;
    }
    int matches(int i, Teams &t1, Teams &t2)
    {
        cout << "\n";
        cout << "                            Final starts   " << endl;
        cout << "                                Enter the no of goals scored by " << t1.team_name << '\n'
             << endl;
        t1.getscore();
        cout << "                               Enter the no of goals scored by " << t2.team_name << '\n'
             << endl;
        t2.getscore();
        if (t1.team_score > t2.team_score)
        {
            cout << "                         " << t1.team_name << " has won Final" << endl;
            return i;
        }
        else if (t1.team_score == t2.team_score)
        {
            cout << "                        "
                 << " Final is draw " << endl;
            cout << "                         Now to make one team winner(knockout tournament) we can increase the score of one team by 1" << endl;
            cout << "                         press any int number except 0 to increase score of team " << t1.team_name << endl;
            cout << "                         press 0 to increase score of team " << t2.team_name << endl;
            int w;
            cin >> w;
            if (w)
            {
                cout << "                     " << t1.team_name << " has won  Final  " << endl;
                return i;
            }
            else
            {
                cout << "                     " << t2.team_name << " has won  Final   " << endl;
                return i + 1;
            }
        }
        else
        {
            cout << "                         " << t2.team_name << " has won  Final  " << endl;
            return i + 1;
        }
    }
};

void leaderboard()
{
    ifstream fin;
    fin.open("sample.txt", ios::in);
    char ch;
    while (!fin.eof())
    {
        ch = fin.get();
        cout << ch;
    }
}
void programmenu()
{
    int expression = -1;
    cout << "MENU: \n 1. Continue with next match \n 2. Current Leaderboard \n 0. Exit program" << endl;
    while (expression != 1)
    {
        cout << "Enter the choice: ";
        cin >> expression;
        switch (expression)
        {
        case 1:
            break;
        case 2:
            leaderboard();
            break;

        case 0:
            exit(0);
        }
    }
}

int main()
{
    cout << "---------------------------------------------- KNOCKOUT TOURNAMENT ------------------------------------" << endl;
    cout << "                                   This tournament will consist of 8 Teams                              " << endl;
    cout << "                       Their will be total of 7 matches i.e 4 Quarterfinals , 2 Semifinals and a Final              " << endl;
    cout << "\n \n \n";
    Teams tq[8];
    Teams ts[4];
    Teams tf[2];
    match *m;
    Quarterfinal q;
    m = &q;
    Semifinals s;
    Final f;
    ofstream fout;
    cout << "                           Enter the 8 teams that will participate in the knockout tournament                       " << endl;
    for (int i = 0; i < 8; i++)
    {
        tq[i].getname();
    }
    for (int i = 0; i < 8; i = i + 2)
    {
        m->showmatches(tq[i], tq[i + 1]);
    }
    int j = 0;
    int e = 1;
    fout << "Quarterfinals starts" << endl
         << endl;
    for (int i = 0; i < 8; i = i + 2)
    {
        fout.open("sample.txt", ios::app);
        int k = q.matches(i, tq[i], tq[i + 1]);
        fout << "Quarterfinal " << e << " ->" << tq[i].team_name << "  V/S " << tq[i + 1].team_name << endl;
        fout << tq[i].team_name << " SCORE: " << tq[i].team_score << endl;
        fout << tq[i + 1].team_name << " SCORE: " << tq[i + 1].team_score << endl;
        fout << "Quarterfinal " << e << " won by " << tq[k].team_name << endl;
        fout.close();
        ts[j] = tq[k];
        programmenu();
        j++;
        e++;
 }
cout << endl
     << endl;
for (int i = 0; i < 4; i = i + 2)
{
    s.showmatches(ts[i], ts[i + 1]);
}
int l = 0;
int d = 1;
fout<<"Semifinals starts"<<endl<<endl;
for (int i = 0; i < 4; i = i + 2)
{
    fout.open("sample.txt", ios::app);
    int k = s.matches(i, ts[i], ts[i + 1]);

    fout << "Semifinal " << d << " ->" << ts[i].team_name << "  V/S " << ts[i + 1].team_name << endl;
    fout << ts[i].team_name << " SCORE: " << ts[i].team_score << endl;
    fout << ts[i + 1].team_name << " SCORE: " << ts[i + 1].team_score << endl;
    fout << "Semifinal " << d << " won by " << ts[k].team_name << endl;
    fout.close();
    tf[l] = tq[k];
     programmenu();
    l++;
    d++;
}
cout << "\n \n";
int i = 0;
f.showmatches(tf[i], tf[i + 1]);
fout.open("sample.txt", ios::app);
int k = f.matches(i, tf[i], tf[i + 1]);
string finalteam = tf[k];
fout << "Final starts" << endl
     << endl;
fout << "Final "
     << " ->" << tf[i].team_name << "  V/S " << tf[i + 1].team_name << endl;
fout << tf[i].team_name << " SCORE: " << tf[i].team_score << endl;
fout << tf[i + 1].team_name << " SCORE: " << tf[i + 1].team_score << endl;
fout << "Final "
     << " won by " << finalteam << endl;
fout.close();

```
