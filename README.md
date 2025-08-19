# Virtual-Train-Route-Planner
This project uses the Doubly Linked List data structure to create a menu-driven simulation of a Train route planner. Users can construct a virtual railroad track, move between stations, and see the trip in real time.  

This is a simple Python script that simulates a train route planner. It makes use of two basic data structures, a doubly linked list for linear routes and a circular linked list for looping routes. It has been done in such a way to present a clear example of how data structures can be leveraged to solve a real world navigational problem.


**Features**
Linear Route: A doubly linked list is used to create a linear path of train stations with a direction.


Loop Route: A circular linked list is used to create a looping train station path which connects the final station back to the first station.


Bidirectional Navigation: In linear route described by a doubly linked list, the user may navigate forwards and backwards. 


Route Printed Clearly: Printed functions are included to clearly print out the order of stations for both types of routes.


**How To Run**
Save it: Save the provided Python code to a file train_planner.py.


Run from the terminal: Open your terminal or command prompt and navigate to the directory you saved the files.


Run the script: To run the script, execute the following command using the Python interpreter:


python train_planner.py


** Example Output**
When you run the script, you'll see a clear separation of the two different routes and their station order, similar to the output below:
Main Route:
Central Station -> Northwood -> Riverbend -> Oakville

Loop Route:
Park Loop -> Lake Loop -> Forest Loop -> (Loop)
