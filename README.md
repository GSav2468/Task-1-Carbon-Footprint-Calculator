#include <iostream>
#include <string>
using namespace std;

double collectUserData(string prompt) {
    double value = 0;
    cout << prompt << endl;
    cin >> value;
    return value;
}

double calculateTotalEmissions(double carMiles, double electricityKwh) {
    return (carMiles * 0.25) + (electricityKwh * 0.20);
}

string classifyEmissions(double total) {
    if (total < 100) {
        return "Low";
    } else if (total <= 300) {
        return "Moderate";
    } else {
        return "High";
    }
}

int main() {
    double carMiles = collectUserData("Monthly car miles travelled:");
    if (cin.fail() || carMiles < 0) {
        cout << "Please run again and enter a number of zero or more." << endl;
        return 1;
    }

    double electricityKwh = collectUserData("Monthly electricity usage (kWh):");
    if (cin.fail() || electricityKwh < 0) {
        cout << "Please run again and enter a number of zero or more." << endl;
        return 1;
    }

    double total = calculateTotalEmissions(carMiles, electricityKwh);
    string classification = classifyEmissions(total);
    cout << "Total monthly emissions: " << total << endl;
    cout << "Classification: " << classification << endl;
    return 0;
}
