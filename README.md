#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

int main()
{
    int products = 0, days = 0;

    cout << "Enter number of products: ";
    cin >> products;
    cout << "Enter number of days: ";
    cin >> days;
    cout << endl;
    float price[products][days];

    cout << "Enter daily sales:" << endl;
    for(int i = 0; i < products; i++){
        cout << "Product " << i + 1 << ": ";
        for (int j = 0; j < days; j++){
            cin >> price[i][j];
        }
    }


    cout << left << setw(10) << "Product";
    for (int j = 0; j < days; j++){
        string day = "Day " + to_string(j + 1);
        cout << setw(10) << day;
    }
    cout << setw(10) << "Total";
    cout << setw(10) << "Average" << endl;
    cout << "---------------------------------------------------------------\n";
    cout << fixed << setprecision(2);
    int best = 0;
    float maxProduct = 0.00;
    float maxday = 0.00;
    int highday = 0;
    for (int i = 0; i < products; i++){
        float total = 0.00;
        cout << left;
        cout << setw(10) << i + 1;
        for (int j = 0; j < days; j++){
            cout << setw(10) << price[i][j];
            total += price[i][j];
        }
        float average = 0.00;
        average = total/days;
        cout << setw(10) << total;
        cout << setw(10) << average << endl;
        average = 0.00;
        if(maxProduct < total){
            maxProduct = total;
            best = i;
        }
    }
    cout << setprecision(0);
    cout << "Total per day:" << endl;
    for (int j = 0; j < days; j++) {
        float totalDay = 0.00;
        for (int i = 0; i < products; i++){
            totalDay += price[i][j];
        }
        cout << "Day " << j + 1 << ": " << totalDay << endl;
        if(maxday < totalDay){
            maxday = totalDay;
            highday = j;
        }
    }
    cout << endl;
    cout << "Best-Selling Product: Product " << best + 1 << endl;
    cout << "Highest Sales Day: Day " << highday + 1;

    return 0;
}
