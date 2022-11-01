```cpp
// Football Knockout tournament simulation project
#include<iostream>
#include<cstring>
using namespace std;
class Teams{
    public:

 string team_name;
public:
    void getname(){
    cin>>team_name;
    }
    operator string(){
    return team_name;
    }
};
class match:public Teams{
public:
    int team_score1;
    int team_score2;
    virtual int matches(int i,Teams t1,Teams t2)=0;

};
class Quarterfinal:public match{
protected:
    int l=1;
public:
    void showmatches(Teams t1,Teams t2){
        cout<<"                            Quarterfinal "<<l<<"  will be played between   ";
    cout<<t1.team_name<<" "<<"v/s"<<" "<<t2.team_name<<endl;
    l++;
    }
int k=1;
    int matches(int i,Teams t1,Teams t2){
        cout<<endl;
        cout<<"                            Quarterfinal "<<k<< " starts   "<<endl;
    cout<<"                                Enter the no of goals scored by "<<t1.team_name<<endl<<endl;
    cin>>team_score1;
     cout<<"                               Enter the no of goals scored by "<<t2.team_name<<endl<<endl;
    cin>>team_score2;
    if(team_score1>team_score2){
        cout<< "                         "<<t1.team_name<<"   "<<"have won Quarterfinal  "<<k<<endl;
        k++;
        return i;
    }
    else if(team_score1==team_score2){
        cout<<"                        "<<"Quarterfinal "<<k<<"is draw "<<endl;
        cout<<"                         Now to make one team winner(knockout tournament) we can increase the score of one team by 1"<<endl;
        cout<<"                         press any int number except 0 to increase score of team "<<t1.team_name<<endl;
        cout<<"                         press 0 to increase score of team "<<t2.team_name<<endl;
        int w;
        cin>>w;
        if(w){
            cout<< "                     "<<t1.team_name<<" "<<"have won Quarterfinal "<<k<<endl;
            k++;
        return i;
        }
        else{

            cout<< "                     "<<t2.team_name<<" "<<"have won Quarterfinal  "<<k<<endl;
            k++;
        return i+1;
        }

    }
    else {
        cout<< "                         "<<t2.team_name<<" "<<"have won Quarterfinal  "<<k<<endl;
        k++;
        return i+1;
    }
    }
};
class Semifinals:public match{
protected :
    int l=1;
public:
    void showmatches(Teams t1,Teams t2){
        cout<<"                            Semifinal "<<l<<"  will be played between   ";
    cout<<t1.team_name<<" "<<"v/s"<<" "<<t2.team_name<<endl;
    l++;
    }
     int matches(int i,Teams t1,Teams t2){
        cout<<endl;
        int k=1;
        cout<<"                            Semifinal "<<k<< " starts   "<<endl;
    cout<<"                                Enter the no of goals scored by "<<t1.team_name<<endl<<endl;
    cin>>team_score1;
     cout<<"                               Enter the no of goals scored by "<<t2.team_name<<endl<<endl;
    cin>>team_score2;
    if(team_score1>team_score2){
        cout<< "                         "<<t1.team_name<<"   "<<"have won  Semifinal  "<<k<<endl;
        k++;
        return i;
    }
    else if(team_score1=team_score2){
        cout<<"                        "<<" Semifinal "<<k<<"is draw "<<endl;
        cout<<"                         Now to make one team winner(knockout tournament) we can increase the score of one team by 1"<<endl;
        cout<<"                         press any int number except 0 to increase score of team "<<t1.team_name<<endl;
        cout<<"                         press 0 to increase score of team "<<t2.team_name<<endl;
        int w;
        cin>>w;
        if(w){
            cout<< "                     "<<t1.team_name<<" "<<"have won  Semifinal "<<k<<endl;
            k++;
        return i;
        }
        else{
                        cout<< "                     "<<t2.team_name<<" "<<"have won  Semifinal  "<<k<<endl;
            k++;
        return i+1;
        }

    }
    else {
        cout<< "                         "<<t2.team_name<<" "<<"have won  Semifinal  "<<k<<endl;
        k++;
        return i+1;
    }
    }

};
class Final:public match{
public:
    void showmatches(Teams t1,Teams t2){
        cout<<"                                 final will be played between   ";
    cout<<t1.team_name<<" "<<"v/s"<<" "<<t2.team_name<<endl;
    }
     int matches(int i,Teams t1,Teams t2){
        cout<<endl;
        cout<<"                            Final starts   "<<endl;
    cout<<"                                Enter the no of goals scored by "<<t1.team_name<<endl<<endl;
    cin>>team_score1;
     cout<<"                               Enter the no of goals scored by "<<t2.team_name<<endl<<endl;
    cin>>team_score2;
    if(team_score1>team_score2){
        cout<< "                         "<<t1.team_name<<"   "<<"  have won  Final    "<<endl;
        return i;
    }
    else if(team_score1=team_score2){
        cout<<"                        "<<" Final is draw "<<endl;
        cout<<"                         Now to make one team winner(knockout tournament) we can increase the score of one team by 1"<<endl;
        cout<<"                         press any int number except 0 to increase score of team "<<t1.team_name<<endl;
        cout<<"                         press 0 to increase score of team "<<t2.team_name<<endl;
        int w;
        cin>>w;
        if(w){
            cout<< "                     "<<t1.team_name<<" "<<"  have won  Final  "<<endl;
        return i;
        }
        else{
            cout<< "                     "<<t2.team_name<<" "<<"  have won  Final   "<<endl;
        return i+1;
        }

    }
    else {
        cout<< "                         "<<t2.team_name<<" "<<"have won  Final  "<<endl;
        return i+1;
    }
    }

};

int main(){
    cout<<"---------------------------------------------- KNOCKOUT TOURNAMENT ------------------------------------"<<endl;
    cout<<"                                   This tournament will consist of 8 Teams                              "<<endl;
    cout<<"                       Their will be total of 7 matches i.e 4 Quarterfinals , 2 Semifinals and a Final   "<<endl;
    cout<<endl<<endl<<endl;
     Teams tq[8];
    Teams ts[4];
    Teams tf[2];
    Quarterfinal q;
    Semifinals s;
    Final f;
     cout<<"                           Enter the 8 teams that will participate in the knockout tournament          "<<endl;
    for(int i=0;i<8;i++){
        tq[i].getname();
    }
    for(int i=0;i<8;i=i+2){
    q.showmatches(tq[i],tq[i+1]);
    }
    int j=0;
    for(int i=0;i<8;i=i+2){
    int k=q.matches(i,tq[i], tq[i+1]);

        ts[j]=tq[k];
        j++;
    }
    cout<<endl<<endl;
     for(int i=0;i<4;i=i+2){
        s.showmatches(ts[i],ts[i+1]);
     }
     int l=0;
    for(int i=0;i<4;i=i+2){

    int k=s.matches(i, ts[i], ts[i+1]);

        tf[l]=tq[k];
        l++;
    }
     cout<<endl<<endl;
    int i=0;
        f.showmatches(tf[i],tf[i+1]);
    int k=f.matches(i, tf[i], tf[i+1]);
        string finalteam=tf[k];
        cout<<finalteam<<" "<<endl;
    }

```
