#include <iostream>
#include <string>
#include <algorithm>
#include <vector>
#include <iomanip>  // Required for setprecision

using namespace std;

// Function Prototypes
float calculateAverage(float g1, float g2, float g3, float g4, float g5);
float findHighest(float g1, float g2, float g3, float g4, float g5);
float findLowest(float g1, float g2, float g3, float g4, float g5);
float getGrade(float average);
int countPassing(float g1, float g2, float g3, float g4, float g5);
float convertToGWA(float average);
bool qualifiesForDL(float gwa);
float validateInput(string subject);

int main() {
    // Student Profile Setup
    string name, id;
    int age, gradeLevel;

    cout << "========================================" << endl;
    cout << "        STUDENT GRADE CALCULATOR" << endl;
    cout << "========================================" << endl << endl;

    cout << "=== STUDENT PROFILE SETUP ===" << endl;
    cout << "Enter student name: ";
    getline(cin, name);
    cout << "Enter student ID: ";
    getline(cin, id);
    cout << "Enter student age: ";
    cin >> age;
    cout << "Enter grade level: ";
    cin >> gradeLevel;
    cin.ignore(); // Consume the newline character

    cout << "\nProfile created successfully!\n" << endl;

    // Grade Entry with Input Validation
    cout << "=== GRADE ENTRY ===" << endl;
    float mathGrade = validateInput("Math");
    float scienceGrade = validateInput("Science");
    float englishGrade = validateInput("English");
    float historyGrade = validateInput("History");
    float artGrade = validateInput("Art");

    cout << "\nGrades recorded successfully!\n" << endl;

    // Basic Statistics Calculation
    float averageGrade = calculateAverage(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    float highestGrade = findHighest(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    float lowestGrade = findLowest(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    int passingSubjects = countPassing(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    float gradeEquivalent = getGrade(averageGrade);

    // Advanced Feature: GPA Conversion
    float gwa = convertToGWA(averageGrade);

    // Data Display
    cout << "========================================" << endl;
    cout << "            STUDENT REPORT CARD" << endl;
    cout << "========================================" << endl << endl;

    cout << "STUDENT INFORMATION:" << endl;
    cout << "Name: " << name << endl;
    cout << "ID: " << id << endl;
    cout << "Age: " << age << " years old" << endl;
    cout << "Grade Level: " << gradeLevel << "th Grade" << endl;
    cout << "Birth Year: " << (2024 - age) << endl << endl;

    cout << "SUBJECT GRADES:" << endl;
    cout << "Math: " << fixed << setprecision(1) << mathGrade << "%" << endl;
    cout << "Science: " << fixed << setprecision(1) << scienceGrade << "%" << endl;
    cout << "English: " << fixed << setprecision(1) << englishGrade << "%" << endl;
    cout << "History: " << fixed << setprecision(1) << historyGrade << "%" << endl;
    cout << "Art: " << fixed << setprecision(1) << artGrade << "%" << endl << endl;

    cout << "GRADE STATISTICS:" << endl;
    cout << "Average Grade: " << fixed << setprecision(1) << averageGrade << "%" << endl;
    cout << "Grade Equivalent: " << fixed << setprecision(3) << gradeEquivalent << endl;
    cout << "Highest Grade: " << fixed << setprecision(1) << highestGrade << "%" << endl;
    string highestSubject;
       if (highestGrade == mathGrade) highestSubject = "Math";
    else if (highestGrade == scienceGrade) highestSubject = "Science";
    else if (highestGrade == englishGrade) highestSubject = "English";
    else if (highestGrade == historyGrade) highestSubject = "History";
    else highestSubject = "Art";
    cout << " (" << highestSubject << ")" << endl;

    cout << "Lowest Grade: " << fixed << setprecision(1) << lowestGrade << "%" << endl;
     string lowestSubject;
       if (lowestGrade == mathGrade) lowestSubject = "Math";
    else if (lowestGrade == scienceGrade) lowestSubject = "Science";
    else if (lowestGrade == englishGrade) lowestSubject = "English";
    else if (lowestGrade == historyGrade) lowestSubject = "History";
    else lowestSubject = "Art";
    cout << " (" << lowestSubject << ")" << endl;
    cout << "Subjects Passing: " << passingSubjects << " out of 5" << endl << endl;

    cout << "GWA: " << fixed << setprecision(3) << gwa << endl;

    // Advanced Feature: Director's List Check
    if (qualifiesForDL(gwa)) {
        cout << "Director's List Status: YES (Congratulations!)" << endl;
    } else {
        cout << "Director's List Status: NO" << endl;
    }

    return 0;
}

// Function Implementations
float calculateAverage(float g1, float g2, float g3, float g4, float g5) {
    return (g1 + g2 + g3 + g4 + g5) / 5.0;
}

float findHighest(float g1, float g2, float g3, float g4, float g5) {
    return max({g1, g2, g3, g4, g5});
}


