# Login & Registration System – C++ (Internship Project)
📌 Project Overview

The Login & Registration System is a console-based C++ application developed as part of my internship tasks at Code Alpha.
This program allows users to register with a unique username and password and log in using stored credentials.

It applies file handling for persistent storage and includes input validation to ensure secure and accurate authentication.

⚙️ Features

• Accepts user registration input (username & password)
• Prevents duplicate usernames
• Stores credentials securely in a text file (users.txt)
• Validates login credentials
• Displays appropriate success or error messages
• Menu-driven console interface
• Colorful UI for better readability

🧮 Authentication Logic

Registration

User enters username and password

System checks if the username already exists

Credentials are stored in users.txt if valid

Login

User enters username and password

System verifies credentials against stored records

Displays success or error messages

🛠 Technologies Used

C++

File Handling (ifstream, ofstream)

Standard Template Library (STL)

Console-based User Interface with ANSI color codes

▶ How to Run

Compile the program:

g++ login_registration.cpp -o login_registration

Run the executable:

./login_registration
📚 Learning Outcomes

Implemented basic authentication logic

Applied file handling for persistent data storage

Strengthened understanding of input validation

Developed a menu-driven and modular console application

Enhanced user experience with colored console output

👩‍💻 Author

Hiba Zia
Internship Task – Code Alpha
