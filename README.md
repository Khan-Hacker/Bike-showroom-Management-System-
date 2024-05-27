# Bike-showroom-Management-System-


#include<iostream>
#include<conio.h>
#include<string>
using namespace std;

struct history {
    string name;
    string prof;
    string bikeCpy;
    string bikeclr;
    float modelno;
    int cc;
    long engineno;
    long price;
    long tprice;

    void input() {
        cout << "Customer name:";
        cin >> name;
        cout << "Customer profession:";
        cin >> prof;
    }

    void output() {
        cout << "\nCustomer name:" << name;
        cout << "\nCustomer profession:" << prof;
        cout << "\n\nBike company is :" << bikeCpy;
        cout << "\nBike colour is :" << bikeclr;
        cout << "\nBike model is :" << modelno;
        cout << "\nBike CC is :" << cc;
        cout << "\nBike engine number is :" << engineno;
        cout << "\nBike Price is :" << price << " pkr";
        cout << "\nBike Total Price is :" << tprice << " pkr";
    }
} a[50] = { {"nasir","teacher","Honda","Red",2020,125,37402,100000},
            {"nadir","lawyer","Yamaha","Black",2019,125,37405,150000},
            {"saim","husband","Suzuki","Blue",2021,150,37403,200000} };

struct Stocks {
    string bikeCpy;
    string bikeclr;
    float modelno;
    int cc;
    long engineno;
    long price;

    void input() {
        cout << "\nEnter Bike Company :";
        cin >> bikeCpy;
        cout << "\nEnter Bike colour :";
        cin >> bikeclr;
        cout << "\nEnter Bike model :";
        cin >> modelno;
        cout << "\nEnter CC :";
        cin >> cc;
        cout << "\nEnter Engine number :";
        cin >> engineno;
        cout << "\nEnter Price";
        cin >> price;
    }

    void output() {
        cout << "\n\nBike company is :" << bikeCpy;
        cout << "\nBike colour is :" << bikeclr;
        cout << "\nBike model is :" << modelno;
        cout << "\nBike CC is :" << cc;
        cout << "\nBike engine number is :" << engineno;
        cout << "\nBike Price is :" << price << " pkr";
    }
} Avbitems[50] = { {"Honda","Red",2020,125,37402,100000},
                   {"Yamaha","Black",2019,125,37405,150000},
                   {"Suzuki","Blue",2021,150,37403,200000} };

void menu();
void show();
void newp();
void billing();

int main() {
    int choice;
    do {
        getch();
        menu();
        cin >> choice;
        switch (choice) {
            case 1:
                show();
                break;
            case 2:
                billing();
                break;
            case 3:
                newp();
                break;
            case 6:
                exit(0);
                break;
            default:
                cout << "\nInvalid value";
                break;
        }
        getch();
    } while (true);
}

void menu() {
    system("cls");
    cout << "\n**************************************************************************************************";
    cout << "\n\nPress 1 for Stock";
    cout << "\nPress 2 if you wanna buy a bike";
    cout << "\nPress 3 to add new stock";
    cout << "\nPress 6 to exit" << endl;
    cout << "\n**************************************************************************************************\n";
}

void show() {
    for (int i = 0; i < 50; i++) {
        if (Avbitems[i].engineno != 0) {
            Avbitems[i].output();
        }
    }
}

void newp() {
    static int count = 3; // Static to retain value across calls
    Avbitems[count].input();
    Avbitems[count].output();
    count++;
}

void billing() {
    long ingnumber;
    bool status = false;
    cout << "\nEnter engine number:";
    cin >> ingnumber;
    for (int i = 0; i < 50; i++) {
        if (Avbitems[i].engineno == ingnumber) {
            a[i].input();
            // Directly copy the details
            a[i].bikeclr = Avbitems[i].bikeclr;
            a[i].bikeCpy = Avbitems[i].bikeCpy;
            a[i].cc = Avbitems[i].cc;
            a[i].engineno = Avbitems[i].engineno;
            a[i].modelno = Avbitems[i].modelno;
            a[i].price = Avbitems[i].price;
            a[i].tprice = Avbitems[i].price;
            a[i].output();
            status = true;
            break;
        }
    }
    if (!status) {
        cout << "\nWrong entry";
    }
}
