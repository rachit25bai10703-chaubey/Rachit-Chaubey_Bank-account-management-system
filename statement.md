Train Ticket Registration System
Statement of Purpose
Project Overview
The Train Ticket Registration System is a console-based application developed in Python 2.x that provides a comprehensive platform for managing train ticket reservations. The system facilitates interaction between three types of users: Administrators, Customers, and Ticket Checkers (TC), each with distinct roles and functionalities.

Objectives
Streamline Ticket Booking Process: Enable customers to search for train routes and book tickets efficiently.

Administrative Control: Allow administrators to manage train routes and locations within the system.

Ticket Verification: Provide ticket checkers with tools to validate passenger tickets using PNR numbers.

Data Persistence: Maintain user information and booking records using pickle file serialization.

Digital Ticket Generation: Generate QR codes containing ticket information for easy verification.

System Features
1. User Management
Administrator
Sign up with personal details (Name, Phone, Address, Email)
Secure login with username and password
Add new locations to the railway network
Create new train routes between locations
Manage existing routes (Update/Delete)
Customer
Register as a new customer
Login to access booking services
Search for available train routes
Book tickets by providing travel details
View booking history
Receive QR code tickets with unique PNR numbers
Ticket Checker (TC)
Register and login to the system
Verify tickets by searching PNR numbers in the database
View ticket details for validation purposes
2. Route Management
Add Location: Administrators can add new stations/locations
Create Route: Define source and destination for train routes
Modify Route: Update source or destination of existing routes
Delete Route: Remove routes from the system
3. Ticket Booking
Route availability verification
Ticket reservation with:
Travel Class selection
Boarding point specification
Quota selection
Automatic PNR generation (10-digit random number)
QR code generation containing ticket details
Technical Specifications
Technology Stack
Component	Technology
Programming Language	Python 2.x
Data Storage	Pickle Files
QR Code Generation	qrcode library
File Handling	pathlib
Data Files
File Name	Purpose
AdminInfoList.pickle	Administrator user details
Admindict.pickle	Admin login credentials
CustInfoList.pickle	Customer user details
custdict.pickle	Customer login credentials
TcInfoList.pickle	Ticket Checker user details
tcdict.pickle	TC login credentials
Route.pickle	Train route information
ticket_list.pickle	Booked ticket records
pnr.pickle	Generated PNR numbers
System Architecture
text

Train_Ticket_System/
│
├── main.py              # Main application file
├── user.py              # User class definition
├── tkt_bk.py            # TICKET_BOOK class definition
│
├── Data Files/
│   ├── AdminInfoList.pickle
│   ├── Admindict.pickle
│   ├── CustInfoList.pickle
│   ├── custdict.pickle
│   ├── TcInfoList.pickle
│   ├── tcdict.pickle
│   ├── Route.pickle
│   ├── ticket_list.pickle
│   └── pnr.pickle
│
└── Generated QR Codes/
    └── [user_named_files].jpg
Class Structure
Train_Ticket Class
Class Variables:

Admin_list - List of admin User objects
Cust_list - List of customer User objects
Tc_list - List of ticket checker User objects
ticket_list - List of booked tickets
loc_list - List of available locations
pnr - List of generated PNR numbers
Methods:

Method	Description
Admin_SignUp()	Register new administrator
Cust_SignUp()	Register new customer
Tc_SignUp()	Register new ticket checker
ADlogin()	Administrator login and dashboard
CUSlogin()	Customer login and booking interface
TClogin()	Ticket checker login and verification
ticket_book()	Process ticket booking and generate QR
User Flow Diagrams
Main Menu Flow
text

┌─────────────────┐
│   Main Menu     │
├─────────────────┤
│ 1. Admin        │──→ Login/SignUp ──→ Route Management
│ 2. Customer     │──→ Login/SignUp ──→ Book Ticket/History
│ 3. TC           │──→ Login/SignUp ──→ Verify Tickets
│ 0. Exit         │──→ End Program
└─────────────────┘
Ticket Booking Flow
text

Customer Login ──→ Select "Book Ticket" ──→ Enter Route Details
                                                    │
                                                    ▼
                                          Route Verification
                                                    │
                                          ┌─────────┴─────────┐
                                          │                   │
                                       Available          Not Available
                                          │                   │
                                          ▼                   ▼
                                   Enter Booking         Error Message
                                   Details (Class,
                                   Boarding Point,
                                   Quota)
                                          │
                                          ▼
                                   Generate PNR &
                                   QR Code
                                          │
                                          ▼
                                   Save Ticket &
                                   Confirm Booking
Dependencies
text

pickle      - Built-in (Data serialization)
qrcode      - External (QR code generation)
random      - Built-in (PNR generation)
pathlib     - Built-in (File path operations)
Installation
Bash

pip install qrcode
pip install pillow  # Required for qrcode image generation
Security Considerations
Password Storage: Passwords are stored in plain text within pickle files (Not recommended for production)
File-based Storage: Data persistence relies on local pickle files
No Encryption: Sensitive data is not encrypted
Recommended Improvements
Implement password hashing (e.g., bcrypt)
Use a proper database (SQLite, MySQL, PostgreSQL)
Add input validation and sanitization
Implement session management
Limitations
Single-user file access (no concurrent user handling)
Python 2.x syntax (deprecated)
No payment gateway integration
Limited route information (no timing, pricing, seat availability)
No ticket cancellation feature
Console-based interface only
Future Enhancements
 Migrate to Python 3.x
 Implement database backend
 Add seat selection and availability
 Include train timing and scheduling
 Payment gateway integration
 Ticket cancellation and refund
 Email/SMS notifications
 Web-based or GUI interface
 Multi-language support
How to Run
Bash

# Ensure Python 2.x is installed
python main.py

# Or for Python 3.x (after migration)
python3 main.py
Authors
[Your Name/Team Name]

Version
1.0.0

License
[Specify License - MIT, GPL, etc.]

Conclusion
The Train Ticket Registration System provides a foundational framework for managing train ticket reservations. While it demonstrates core concepts of user management, data persistence, and ticket generation, it requires significant enhancements for production deployment, particularly in areas of security, scalability, and user experience.