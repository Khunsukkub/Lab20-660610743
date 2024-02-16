#include<iostream>
#include<fstream>
#include<vector>
#include<string>
#include<cstdlib>

using namespace std;

char score2grade(int score){
    if(score >= 80) return 'A';
    if(score >= 70) return 'B';
    if(score >= 60) return 'C';
    if(score >= 50) return 'D';
    else return 'F';
}

string toUpperStr(string x){
    string y = x;
    for(unsigned i = 0; i < x.size();i++) y[i] = toupper(x[i]);
    return y;
}

void importDataFromFile(string filename, vector<string>& names, vector<int>& scores, vector<char>& grades) {
    ifstream info(filename);
    
    string line;
    
    char name[100];
    
    int grade1, grade2, grade3;
    
    while(getline(info, line)) {
        sscanf(line.c_str(), "%[^:]: %d %d %d", name, &grade1, &grade2, &grade3);
        names.push_back(name);
        int gradesum = grade1 + grade2 + grade3;
        scores.push_back(gradesum);
        grades.push_back(score2grade(gradesum));
    }
}


void getCommand(string &command, string &key){
    string line;
    
    cout << "Please input your command: ";
    getline(cin, line);
    
    int space = line.find(' ');
    
    if (space == 0) {
        command = line;
        key = "";
    } else {

        command = line.substr(0, space);
        key = line.substr(space + 1);
        
    }

}



void searchName(vector<string> names, vector<int> scores, vector<char> grades, string key){
    vector<string> namu = names;
    for (auto& name : namu) {
        name = toUpperStr(name);
    }
    key = toUpperStr(key);
    unsigned int i = 0;
    while(i < names.size()){
        if(namu[i] == key){
           cout << "---------------------------------" << endl;
           cout << names[i] << "'s score = " << scores[i] << endl;
           cout << names[i] << "'s grade = " << grades[i] << endl;
            cout << "---------------------------------" << endl;
            break;
        }
        i++;
    }
    
    if(i == names.size()){
        cout << "---------------------------------" << endl;
        cout << "Cannot found." << endl;
        cout << "---------------------------------" << endl;
    }
}
    

void searchGrade(vector<string> &names, vector<int> &scores, vector<char> &grades, string key){

    key = toUpperStr(key);
    unsigned int i = 0;
    int count = 0;
    cout << "---------------------------------" << endl;
    
    while(i < grades.size()){
        if(grades[i] >= 'a' && grades[i] <= 'z'){
            grades[i] -= 32;
        }
        if(grades[i] == key[0]){

            cout << names[i] << " (" << scores[i] << ")" << endl;
            count += 1;
        }
        i++;
    }
    if(i == grades.size() && count == 0){
        cout << "Cannot found." << endl;
    }
    cout << "---------------------------------" << endl;
}


int main(){
    string filename = "name_score.txt";
    vector<string> names;
    vector<int> scores;
    vector<char> grades; 
    importDataFromFile(filename, names, scores, grades);
    
    do{
        string command, key;
        getCommand(command,key);
        command = toUpperStr(command);
        key = toUpperStr(key);
        if(command == "EXIT") break;
        else if(command == "GRADE") searchGrade(names, scores, grades, key);
        else if(command == "NAME") searchName(names, scores, grades, key);
        else{
            cout << "---------------------------------\n";
            cout << "Invalid command.\n";
            cout << "---------------------------------\n";
        }
    }while(true);
    
    return 0;
}
