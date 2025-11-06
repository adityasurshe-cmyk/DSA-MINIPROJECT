#include <iostream>
#include <vector>
using namespace std;

struct Student {
    int id;
    string name;
    int age;
    float marks;
};

vector<Student> students;

void addStudent() {
    Student s;
    cout << "Enter ID, Name, Age, and Marks: ";
    cin >> s.id >> s.name >> s.age >> s.marks;
    students.push_back(s);
}

void displayStudents() {
    if (students.empty()) {
        cout << "No students to display.\n";
        return;
    }

    cout << "\n--- Student List ---\n";
    for (auto &s : students)
        cout << "ID: " << s.id << ", Name: " << s.name
             << ", Age: " << s.age << ", Marks: " << s.marks << "\n";
}

void searchStudent() {
    int id;
    cout << "Enter ID to search: ";
    cin >> id;

    for (auto &s : students) {
        if (s.id == id) {
            cout << "Found: ID: " << s.id << ", Name: " << s.name
                 << ", Age: " << s.age << ", Marks: " << s.marks << "\n";
            return;
        }
    }

    cout << "Student not found.\n";
}

int main() {
    int ch;
    do {
        cout << "\n1. Add Student\n2. Display Students\n3. Search Student\n4. Exit\n";
        cout << "Enter choice: ";
        cin >> ch;

        if (ch == 1)
            addStudent();
        else if (ch == 2)
            displayStudents();
        else if (ch == 3)
            searchStudent();
        else if (ch != 4)
            cout << "Invalid choice!\n";

    } while (ch != 4);

    cout << "Exiting program.\n";
    return 0;
}
