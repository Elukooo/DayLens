# DayLens

DayLens is a web application designed to help users log and reflect on their daily activities and experiences. It provides a structured way to track what you create, who you connect with, what you learn, and your meditation practices, along with general notes.

## Features

*   **User Authentication:** Secure sign-up and sign-in with email and password. Supports anonymous guest access and custom token authentication.
*   **Daily Logging:** Create, read, update, and delete daily logs.
*   **Categorized Entries:** Organize your daily reflections into specific categories:
    *   **Create:** What you created or accomplished.
    *   **Connect:** Interactions with people, including notes.
    *   **Learn:** Topics you learned and the methods used.
    *   **Meditate:** Duration and type of meditation.
    *   **Notes:** General thoughts and observations.
*   **Week Navigation:** Easily browse through your logs by week.
*   **Responsive Design:** Built with Tailwind CSS for a modern and adaptable user interface.
*   **Real-time Data:** Utilizes Firebase Firestore for real-time synchronization of your day logs.

## Technologies Used

*   **Frontend:**
    *   HTML5
    *   CSS3 (with Tailwind CSS for utility-first styling)
    *   JavaScript (ES Modules)
*   **Backend/Database:**
    *   Firebase Authentication
    *   Firebase Firestore

## Installation

To set up DayLens locally, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd Daylens2
    ```

3.  **Firebase Configuration:**
    *   Create a new Firebase project in the Firebase Console.
    *   Enable Firebase Authentication (Email/Password and Anonymous).
    *   Enable Firestore Database.
    *   Copy your Firebase project's configuration object and replace the placeholder in `script.js`:
        ```javascript
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_AUTH_DOMAIN",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_STORAGE_BUCKET",
            messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
            appId: "YOUR_APP_ID"
        };
        ```
    *   Set up Firestore Security Rules to protect user data. A basic rule might look like:
        ```
        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            match /artifacts/{appId}/users/{userId}/dayLogs/{document=**} {
              allow read, write: if request.auth != null && request.auth.uid == userId;
            }
          }
        }
        ```

## Usage

Open `index.html` in your web browser. The application will prompt you to log in or sign up. You can also continue as a guest, but your data will not be saved permanently.

## Contributing

Contributions are welcome! Please feel free to open issues or submit pull requests.

## License

This project is open source and available under the [MIT License](LICENSE).
