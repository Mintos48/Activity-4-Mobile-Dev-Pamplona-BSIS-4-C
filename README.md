Photography Service App
Overview
The Photography Service App is a Flutter-based mobile application designed to manage photography orders, reservations, and documents. It features a free login system (no backend or subscription required), a navigation demo, and an interactive TabBar demo. The app starts at an authentication screen, allowing users to log in or register before accessing the main features.
Features

Authentication (Tasks 2, 3, 4):
Free Login: The app uses a client-side authentication system with no backend. Users can log in with any email containing an '@' symbol and any password, or register with basic validation.
Two tabs: Login and Register, implemented in auth_screen.dart.
After successful login/register, navigates to the home screen.


Home Screen (Tasks 5, 6, 7, 9):
Two-tab BottomNavigationBar: Order & Reservation and Tab Demo.
Drawer: Links to Home, About, and Contact screens (named routes).
Logout button returns to the authentication screen.
Tab Demo (Task 9): Interactive TabBar in the AppBar with Chats, Status, and Calls lists, each with SnackBar feedback.


Order & Reservation Screen (Tasks 1, 8, 10):
Three-tab TabBar: Order & Pay, Reservation, and Documents.
Order & Pay: Navigation demo with "Preview Order (Push)" and "Confirm Order (Replace)" buttons, showing push() and pushReplacement() navigation with history tracking.
Reservation: Form for booking sessions with date/time pickers.
Documents: Form for uploading document names (client-side list).


Navigation Demo (Tasks 1, 8):
In the "Order & Pay" tab, demonstrates Navigator.push() (adds a preview screen) and Navigator.pushReplacement() (replaces with a confirmation screen).
Tracks navigation history for push() actions in a ListView.


Additional Screens:
About: Static information about the photography service.
Contact: Static contact details.



Project Structure
lib/
├── main.dart
├── screens/
│   ├── auth_screen.dart
│   ├── home_screen.dart
│   ├── order_reservation_screen.dart
│   ├── about_screen.dart
│   ├── contact_screen.dart


main.dart: Entry point, defines MaterialApp with named routes (/auth, /home, /about, /contact) and starts at /auth.
auth_screen.dart: Authentication screen with Login and Register tabs.
home_screen.dart: Main screen with BottomNavigationBar and TabBar demo.
order_reservation_screen.dart: Order & Reservation screen with navigation demo.
about_screen.dart, contact_screen.dart: Support Drawer navigation.

Authentication Details
The authentication system is implemented in auth_screen.dart and is designed for simplicity, requiring no backend or subscription:

Login Tab:
Fields: Username, Email, Password.
Validation: Email must contain '@' (e.g., user@example.com). No password validation.
Action: On valid email, navigates to /home using Navigator.pushReplacementNamed.
Feedback: Shows a SnackBar if the email is invalid.


Register Tab:
Fields: Name, Email, Password, Confirm Password, Role (dropdown: Admin/User).
Validation:
Name: Non-empty.
Email: Must contain '@'.
Password: Non-empty.
Confirm Password: Must match Password.
Role: Must be selected.


Action: On valid input, shows a SnackBar ("Registration Successful") and navigates to /home.


Free Login: No server-side authentication or user data storage. The system is client-side, allowing instant access for testing or demo purposes.

Setup Instructions
Prerequisites

Flutter SDK: Version 3.0.0 or higher.
Dart: Version 2.17.0 or higher.
IDE: VS Code, Android Studio, or IntelliJ IDEA with Flutter plugin.
Emulator or physical device (Android/iOS).

Installation

Clone the Repository:git clone <repository-url>
cd photography_service_app


Install Dependencies:Ensure pubspec.yaml includes:dependencies:
  flutter:
    sdk: flutter
  intl: ^0.17.0

Run:flutter pub get


File Structure:Place the following files in the correct directories:
lib/main.dart
lib/screens/auth_screen.dart
lib/screens/home_screen.dart
lib/screens/order_reservation_screen.dart
lib/screens/about_screen.dart
lib/screens/contact_screen.dart


Run the App:flutter clean
flutter run



Usage

Authentication:
Launch the app to see AuthScreen (initial route: /auth).
Login: Enter any email with '@' (e.g., test@example.com) and any password. Click "Login" to go to HomeScreen.
Register: Fill in Name, Email (with '@'), Password, Confirm Password (matching), and select a Role. Click "Register" to go to HomeScreen.


Home Screen:
Use the BottomNavigationBar to switch between:
Order & Reservation: Access Order & Pay, Reservation, and Documents tabs.
Tab Demo: View Chats, Status, and Calls lists (Task 9). Tap items to see SnackBar feedback.


Open the Drawer to navigate to Home, About, or Contact.
Click the logout button (top-right) to return to AuthScreen.


Order & Pay (Navigation Demo):
In the "Order & Pay" tab, enter an order description and click "Place Order" to add it to the list.
Use the navigation buttons:
Preview Order (Push): Opens a preview screen (SecondScreen). Back button returns to "Order & Pay". Adds to navigation history.
Confirm Order (Replace): Opens a confirmation screen (SecondScreen). Back button returns to HomeScreen.


View navigation history in the ListView below (only for "Preview Order (Push)").


Reservation:
Enter a username, pick a date and time, and click "Confirm Reservation" to see a SnackBar.


Documents:
Enter a document name and click "Upload Document" to add it to the list.


Tab Demo:
Switch between Chats, Status, and Calls tabs in the AppBar.
Tap list items to see SnackBar feedback (e.g., "Opening chat with Alice").



Testing the App

Authentication:
Test Login with invalid email (no '@') to see SnackBar error.
Test Register with mismatched passwords or empty fields to see validation errors.
Verify navigation to HomeScreen on valid input.


Navigation Demo:
In "Order & Pay", test "Preview Order (Push)":
Confirm SecondScreen opens with "Order Preview" title.
Check back button returns to "Order & Pay".
Verify history updates in the ListView.


Test "Confirm Order (Replace)":
Confirm SecondScreen opens with "Order Confirmation" title.
Check back button returns to HomeScreen.
Ensure no black screen appears.




Tab Demo:
In "Tab Demo", switch between Chats, Status, and Calls.
Tap items to verify SnackBar feedback.


Other Features:
Test Drawer navigation to About and Contact.
Test logout to return to AuthScreen.



Troubleshooting

Black Screen on "Confirm Order (Replace)":
Check the debug console for errors:flutter run --verbose

Look for prints like "Navigating with pushReplacement()", "Building SecondScreen: isPush=false".
If the black screen persists, try removing rootNavigator: true in order_reservation_screen.dart:Navigator.pushReplacement(newContext, MaterialPageRoute(builder: (context) => const SecondScreen(isPush: false)));


Share console logs and device details (Android/iOS, emulator/physical).


Dependencies:
If errors occur, ensure intl: ^0.17.0 is installed and run flutter pub get.


Navigation Issues:
Verify main.dart has correct routes (/auth, /home, /about, /contact).
Ensure flutter clean is run before testing.



Notes

The app is designed for demo purposes with client-side functionality.
No external backend or database is required, making it easy to test.
All tasks (1–10) are implemented:
Task 1, 8: Navigation demo in "Order & Pay".
Task 2, 3, 4: Authentication with Login/Register.
Task 5, 6, 7: Home screen with BottomNavigationBar, Drawer, and named routes.
Task 9: TabBar demo in "Tab Demo".
Task 10: Reservation and Documents tabs.



For issues or contributions, contact support@photoservice.com (demo contact).