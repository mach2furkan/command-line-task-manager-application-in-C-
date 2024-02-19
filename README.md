     #include <iostream>
    #include <fstream>
      #include <vector>
      #include <algorithm>

     using namespace std;

     // Structure to represent a task
        struct Task {
           string title;
    string description;
    int priority;
    string dueDate;
    bool completed;
     };

    // Function to display a task
       void displayTask(const Task& task) {
    cout << "Title: " << task.title << endl;
    cout << "Description: " << task.description << endl;
    cout << "Priority: " << task.priority << endl;
    cout << "Due Date: " << task.dueDate << endl;
    cout << "Completed: " << (task.completed ? "Yes" : "No") << endl;
     }

     // Function to add a new task
      void addTask(vector<Task>& tasks) {
    Task newTask;
    cout << "Enter title: ";
    getline(cin >> ws, newTask.title);
    cout << "Enter description: ";
    getline(cin >> ws, newTask.description);
    cout << "Enter priority (1-5): ";
    cin >> newTask.priority;
    cout << "Enter due date (YYYY-MM-DD): ";
    cin >> newTask.dueDate;
    newTask.completed = false;
    tasks.push_back(newTask);
    cout << "Task added successfully!" << endl;
     }

    // Function to mark a task as completed
      void markTaskCompleted(vector<Task>& tasks) {
    int index;
    cout << "Enter the index of the task to mark as completed: ";
    cin >> index;
    if (index >= 0 && index < tasks.size()) {
        tasks[index].completed = true;
        cout << "Task marked as completed!" << endl;
    } else {
        cout << "Invalid index!" << endl;
    }
      }

     // Function to delete a task
            void deleteTask(vector<Task>& tasks) {
    int index;
    cout << "Enter the index of the task to delete: ";
    cin >> index;
    if (index >= 0 && index < tasks.size()) {
        tasks.erase(tasks.begin() + index);
        cout << "Task deleted successfully!" << endl;
    } else {
        cout << "Invalid index!" << endl;
    }
      }

          // Function to view all tasks
                void viewAllTasks(const vector<Task>& tasks) {
    for (size_t i = 0; i < tasks.size(); ++i) {
        cout << "Task " << i << ":" << endl;
        displayTask(tasks[i]);
        cout << endl;
    }
    }

     int main() {
    vector<Task> tasks;
    int choice;

    do {
        cout << "Task Manager Application" << endl;
        cout << "1. Add Task" << endl;
        cout << "2. Mark Task as Completed" << endl;
        cout << "3. Delete Task" << endl;
        cout << "4. View All Tasks" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                addTask(tasks);
                break;
            case 2:
                markTaskCompleted(tasks);
                break;
            case 3:
                deleteTask(tasks);
                break;
            case 4:
                viewAllTasks(tasks);
                break;
            case 5:
                cout << "Exiting... Goodbye!" << endl;
                break;
            default:
                cout << "Invalid choice! Please enter a number between 1 and 5." << endl;
        }
    } while (choice != 5);

    return 0;
     }
