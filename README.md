/*# athletecreation
for Octathlon project*/
#include<iostream>
#include<fstream>
#include<sstream>
#include<string>
#include<iomanip>
using namespace std;

class Ability
{
    private:
    int speed;
    int strength;
    int endurance;
    int skill;  
    public:
    Ability(int speed, int strength, int endurance, int skill);
};

Ability::Ability(int speed, int strength, int endurance, int skill) 
:speed(speed), strength(strength), endurance(endurance), skill(skill) {};

class Athlete
{
  string gender;
  Ability AthleteAbility;
  int injury;
  int consistency;
  int weariness;
  friend ostream& operator<<(ostream& out, Athlete& ath); 
  friend istream& operator>>(istream& in, Athlete& ath);
  string name;
  unsigned int idnum;
  public:
  Athlete(string name, int idnum, string gender, int speed, int strength, int endurance, int skill, int injury, int consistency, int weariness);
  void display();
  int getAthlete();

};

Athlete::Athlete(string name, int idnum, string gender, int speed, int strength, int endurance, int skill, int injury, int consistency, int weariness)
:name(name), idnum(idnum), gender(gender), AthleteAbility(speed, strength, endurance, skill), injury(injury), consistency(consistency), weariness(weariness){};

ostream& operator<<(ostream &out, Athlete& ath) 
{
    out<<ath.idnum<<" "<<ath.name;
    return out;
}

istream& operator>>(istream &in, Athlete& ath) 
{
    in >> ath.idnum >> ath.name;
    return in;
}

void Athlete::display() 
{
    cout << "Athlete "<< name << "ID: " << idnum << " " << "gender is " << gender << endl;
}

class SupportCrew
{
  string crewName;
  Ability AthleteAbility;
  Athlete SupportAthlete;
  public:
  SupportCrew(string crewName, int speed, int strength, int endurance, int skill, int injury, int consistency, int weariness);
};

/*SupportCrew::SupportCrew(string crewName, int speed, int strength, int endurance, int skill, int injury, int consistency, int weariness)
:crewName(crewName), AthleteAbility(speed, strength, endurance, skill), SupportAthlete(injury, consistency, weariness){};*/
class Trainer : public SupportCrew
{
  string trainerName;
  Ability AthleteAbility;
  Athlete SupportAthlete;
  public:
  Trainer(string trainerName, int speed, int strength, int endurance, int skill, int injury, int consistency, int weariness);
};

class field_Trainer : public Trainer
{
  string trainerName;
  Ability AthleteAbility;
  Athlete SupportAthlete;
  public:
  field_Trainer(string trainerName, int strength, int skill, int injury, int consistency, int weariness);
  field_Trainer &operator++();
};
/*field_Trainer::field_Trainer(string trainerName, int strength, int skill, int consistency)
:trainerName(trainerName), AthleteAbility(strength, skill), SupportAthlete(consistency) {};

field_Trainer& field_Trainer::operator++()
{
  ++consistency;
  ++skill;
  ++strength;
  return *this;
}*/

class track_Trainer : public Trainer
{
  string trainerName;
  Ability AthleteAbility;
  Athlete SupportAthlete;
  public:
  track_Trainer(string trainerName, int speed, int endurance, int injury, int consistency, int weariness);
  track_Trainer &operator++();
};
/*track_Trainer::track_Trainer(string trainerName, int speed, int endurance, int consistency)
:trainerName(trainerName), AthleteAbility(speed, endurance), SupportAthlete(consistency) {};*/

class Team
{

};

int main(int argc, char* argv[])
{
  Athlete femaleAthlete= Athlete("Tanya Powell", 2431, "female", 80, 80, 40, 30,0,20,5);
 /* int counter=1;
  ifstream inFile1;
  inFile1.open(argv[1]);
  string line;
  getline(inFile1,line);
  cout << "File name is female-athletes.txt.\n";
  while(inFile1.good())
	{
		cout << counter++ << "\t:\t" << line << endl;
    cout<< "Athlete # "<< counter++ << ": " << femaleAthlete << endl;
    void displayfemaleAthlete();
    
	}
  inFile1.close();
  cout <<'\n';*/
  femaleAthlete.display();
  
}
