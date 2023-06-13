#include <iostream>
#include <stdio.h>
#include <fstream>
#include <locale.h>

#define CRT_SECURE_NO_WARNINGS

//D:\

using namespace std;

//fstream Database;

ifstream Database;

class member {
public:
    string login, password;
    member() {

    }
    member(string Login, string Password) {
        login = Login;
        password = Password;
    }
};

void write(string input) {
    ofstream Database1;
    Database1.open("Data.txt", ios::app);
    if (Database1.is_open()) {
        Database1 << input << "\n";
    }
    Database1.close();
}

string read(int line) {
    string out;
    Database.open("Data.txt");
    
    for (int i = 0; i < line; i++) {
        Database >> out;
    }

    Database.close();

    return out;
}

int main()
{
    string log, pass;

    int choose;

    while (true) {
        choose = 0;
        cout << "Choose action: 1 - autorisation; 2 - registration; 3 - exit;\n";
        cin >> choose;
        if (choose == 3) return 0;
        member* user = new member;

        int i = 1;
        switch (choose) {
        case(1):
            cout << "Enter login\n";
            cin >> user->login;

            cout << "Searching...\n";

            while (!Database.eof()) {

                log = read(i);
                pass = read(i + 1);

                if (user->login == log) {
                    cout << "Enter password\n";
                    cin >> user->password;
                    if (user->password == pass) {
                        cout << "Hello, dear user!\n";
                        break;
                    }
                    else {
                        cout << "Incorrect password, please try again\n";
                        break;
                    }
                }
                if (log == "") {
                    cout << "Account not alive!";

                    break;
                }

                i += 2;
            }
            break;
        case(2):
            cout << "Enter login\n";
            cin >> user->login;
            
            i = 1;
            while (!Database.eof()) {

                log = read(i);

                if (user->login == log) {
                    cout << "This login is used!\n";
                    i = -1;
                    break;
                }

                i += 2;
            }
            if (i != -1) {
                cout << "Enter password\n";
                cin >> user->password;
                cout << "Creating...\n";

                write(user->login);
                write(user->password);

                cout << "You account was created!\n";

                break;
            }
            else {
                break;
            }
        }
    }
}
