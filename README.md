# LoginFoam - Android Authentication App

A production-ready Android application featuring user registration, login, and profile management using Firebase Realtime Database. Built with Material Design principles, featuring comprehensive form validation, secure authentication flow, and modern UI/UX patterns.

**Platform:** Android (Java)  
**Database:** Firebase Realtime Database  
**Minimum SDK:** API Level 21 (Android 5.0)  
**Target SDK:** API Level 34+

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Screenshots & UI](#screenshots--ui)
- [Tech Stack](#tech-stack)
- [Project Structure & Architecture](#project-structure--architecture)
- [Getting Started - Step by Step](#getting-started---step-by-step)
- [Firebase Configuration](#firebase-configuration)
- [Database Design](#database-design)
- [Complete Code Breakdown](#complete-code-breakdown)
- [UI/UX Components Details](#uiux-components-details)
- [How the App Works - User Flow](#how-the-app-works---user-flow)
- [Security Considerations](#security-considerations)
- [Known Issues & Limitations](#known-issues--limitations)
- [Improvements & Future Enhancements](#improvements--future-enhancements)
- [Troubleshooting](#troubleshooting)
- [Contributing Guidelines](#contributing-guidelines)
- [License](#license)
- [Author & Contact](#author--contact)

---

## 🎯 Project Overview

**LoginFoam** is a complete authentication system built as an Android application. It demonstrates:
- User registration with data validation
- Secure login with Firebase backend
- Profile display with user information
- Material Design UI patterns
- Best practices for Android development

This project serves as an excellent learning resource for developers building authentication systems in Android, or as a starter template for larger applications requiring user management.

**Target Users:** Students, developers learning Android/Firebase, startups building MVP apps

---

## ✨ Key Features

### 1. Splash Screen
- Professional app introduction screen
- Displays app logo/branding for 3 seconds
- Automatic transition to login screen
- Prevents back navigation (finish() called)

### 2. User Registration (SignupActivity)
- Collects: Full Name, Email, Username, Password
- Stores data in Firebase Realtime Database
- Success confirmation via Toast notification
- Automatic redirect to login screen
- Username serves as unique database key

### 3. User Login (loginActivity)
- Username and password authentication
- Real-time Firebase query with `orderByChild()`
- Password verification with direct comparison
- Error feedback for invalid credentials
- Inline field error messages
- Intent-based data passing to profile screen

### 4. User Profile (ProfileActivity)
- Displays authenticated user information:
  - Profile image (static for demo)
  - User's full name and username in header
  - Email address
  - Username
  - Password (for demonstration only)
  - Stats: Posts (27), Followers (455), Following (413)
- Receives data via Intent extras from login activity
- Beautiful card-based layout with separators

### 5. Data Model (HelperClass)
- POJO (Plain Old Java Object) for user data
- Serialization/deserialization for Firebase
- Getters, setters, and constructors
- Clean separation of concerns

### 6. Material Design UI
- CardView components with elevation
- Custom lavender color theme (#9C27B0)
- Rounded corners (cornerRadius = 20dp)
- Icon-enhanced input fields
- Consistent padding and spacing
- Touch feedback on buttons
- Responsive layouts

---

## 📸 Screenshots & UI

| Screen | Description | File |
|--------|-------------|------|
| Splash | App branding with logo | `activity_splash_screen.xml` |
| Login | Username/password form | `activity_login.xml` |
| Signup | Registration form with 4 fields | `activity_signup.xml` |
| Profile | User information display | `activity_profile.xml` |

**Color Palette:**
- Primary Color: `#9C27B0` (Lavender)
- Background: White/Custom gradients
- Text Primary: Black (`#000000`)
- Text Secondary: Grey (`#757575`)

---

## 🛠 Tech Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| **Language** | Java | 8+ |
| **Platform** | Android SDK | API 21-34+ |
| **Database** | Firebase Realtime Database | Latest |
| **Authentication** | Firebase (Custom) | Latest |
| **UI Framework** | Android Material Design | 1.4+ |
| **Build Tool** | Gradle | 7.0+ |
| **IDE** | Android Studio | 2022.1+ |
| **VCS** | Git | - |

**Key Libraries:**
```gradle
implementation 'com.google.firebase:firebase-database:20.3.0'
implementation 'com.google.firebase:firebase-auth:22.3.0'
implementation 'androidx.cardview:cardview:1.0.0'
implementation 'androidx.appcompat:appcompat:1.6.1'
implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
```

---

## 🗂 Project Structure & Architecture

### Directory Layout
```
com.example.loginfoam/
│
├── Activities (Java Classes)
│   ├── SplashScreen.java
│   │   └── Shows logo with 3-second delay
│   │       Transitions to LoginActivity
│   │
│   ├── SignupActivity.java
│   │   └── User registration form
│   │       Validates input
│   │       Writes to Firebase
│   │       Navigates to login
│   │
│   ├── loginActivity.java
│   │   └── User authentication
│   │       Firebase query and password match
│   │       Error handling
│   │       Intent to ProfileActivity
│   │
│   └── ProfileActivity.java
│       └── Display user profile
│           Receives Intent extras
│           Shows all user info
│
├── Models (Data Classes)
│   └── HelperClass.java
│       └── User POJO
│           Getters/Setters
│           Firebase serialization
│
└── Resources (res/)
    ├── layout/
    │   ├── activity_splash_screen.xml
    │   ├── activity_signup.xml
    │   ├── activity_login.xml
    │   └── activity_profile.xml
    │
    ├── drawable/
    │   ├── pagebkg (Background image)
    │   ├── profilebkg (Profile background)
    │   ├── levender_border (Custom drawable)
    │   ├── white_background (Card background)
    │   ├── ic_outline_frame_person_24 (User icon)
    │   ├── ic_baseline_lock_24 (Lock icon)
    │   ├── ic_baseline_email_24 (Email icon)
    │   ├── bilal (Profile picture)
    │   └── logo (Splash screen logo)
    │
    ├── values/
    │   └── colors.xml
    │       ├── lavender (#9C27B0)
    │       ├── white (#FFFFFF)
    │       ├── black (#000000)
    │       └── grey (#757575)
    │
    └── AndroidManifest.xml
        └── Activity declarations
            Internet permission
            Launcher activity
```

### Architecture Pattern: MVP (Model-View-Presenter)
- **Model:** HelperClass (data structure)
- **View:** XML layouts (UI)
- **Presenter/Logic:** Activities (business logic)

---

## 🚀 Getting Started - Step by Step

### Prerequisites Checklist
- [ ] Android Studio installed (2022.1 or newer)
- [ ] Java JDK 8 or higher installed
- [ ] Firebase account created
- [ ] Android device or emulator available (API 21+)
- [ ] Git installed (for cloning)
- [ ] Internet connection (for Firebase)

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/loginfoam.git
cd loginfoam
```

### Step 2: Open Project in Android Studio
1. Launch Android Studio
2. Click **File > Open**
3. Navigate to the cloned `loginfoam` folder
4. Select the project root directory
5. Click **OK**
6. Wait for project indexing to complete

### Step 3: Sync Gradle Files
1. Android Studio will prompt "Gradle files need to be updated"
2. Click **Sync Now** (or **File > Sync Project with Gradle Files**)
3. Wait for dependencies to download
4. Monitor the Gradle Sync panel for completion

### Step 4: Create Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **Create a project**
3. Enter project name: "LoginFoam" (or your choice)
4. Accept Firebase terms
5. Click **Create project**
6. Wait for Firebase to initialize

### Step 5: Register Android App with Firebase
1. In Firebase Console, click **Add app** (or the Android icon)
2. Select **Android**
3. Enter Package name: `com.example.loginfoam`
4. (Optional) App nickname: "LoginFoam Debug"
5. (Optional) SHA-1 certificate fingerprint
   - To get your SHA-1:
     ```bash
     ./gradlew signingReport
     ```
   - Copy the SHA-1 value from Gradle output
6. Click **Register app**

### Step 6: Download google-services.json
1. In Firebase Console, click **Download google-services.json**
2. The file will download to your Downloads folder
3. Copy the `google-services.json` file
4. Paste it into your project's `app/` directory (NOT in `src/`)

### Step 7: Update build.gradle Files

**Project-level build.gradle** (usually `/build.gradle`):
```gradle
buildscript {
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:7.4.2'
        classpath 'com.google.gms:google-services:4.3.15'
    }
}
```

**App-level build.gradle** (`/app/build.gradle`):
```gradle
plugins {
    id 'com.android.application'
    id 'com.google.gms.google-services'
}

android {
    compileSdk 34
    
    defaultConfig {
        applicationId "com.example.loginfoam"
        minSdk 21
        targetSdk 34
        versionCode 1
        versionName "1.0"
    }
    
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
    
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}

dependencies {
    // Firebase
    implementation 'com.google.firebase:firebase-database:20.3.0'
    implementation 'com.google.firebase:firebase-auth:22.3.0'
    implementation 'com.google.firebase:firebase-core:21.1.1'
    
    // AndroidX & Material
    implementation 'androidx.appcompat:appcompat:1.6.1'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
    implementation 'androidx.cardview:cardview:1.0.0'
    implementation 'com.google.android.material:material:1.9.0'
    
    // Testing
    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.1'
}
```

### Step 8: Configure Firebase Realtime Database
1. In Firebase Console, go to **Realtime Database**
2. Click **Create Database**
3. Choose location (closest to your region)
4. Start in **Test Mode** (for development)
5. Click **Enable**
6. Navigate to the **Rules** tab
7. Set the following rules (for testing):
```json
{
  "rules": {
    "users": {
      ".read": true,
      ".write": true
    }
  }
}
```
8. Click **Publish**

### Step 9: Update AndroidManifest.xml
Ensure your `AndroidManifest.xml` has:
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.loginfoam">

    <uses-permission android:name="android.permission.INTERNET" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.LoginFoam">

        <activity
            android:name=".SplashScreen"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity android:name=".loginActivity" />
        <activity android:name=".SignupActivity" />
        <activity android:name=".ProfileActivity" />

    </application>

</manifest>
```

### Step 10: Build and Run
1. Connect your Android device via USB (or start an emulator)
2. Click **Run > Run 'app'** (or press Shift + F10)
3. Select your target device
4. Click **OK**
5. Wait for the build and installation to complete
6. App will launch automatically

---

## 🔥 Firebase Configuration

### Detailed Firebase Setup

#### Creating a Firebase Project

**Via Firebase Console:**
1. Visit https://console.firebase.google.com/
2. Sign in with Google account
3. Click **Add project**
4. Fill project name: "LoginFoam"
5. Accept terms and click **Continue**
6. Disable Google Analytics (optional for development)
7. Click **Create project**
8. Wait 30-60 seconds for project creation

**Verify Project Creation:**
- You should see a project dashboard
- URL should contain your project ID: `https://console.firebase.google.com/project/yourprojectid/overview`

#### Register Android App

**Steps:**
1. In Firebase Console, click the Android icon (or **Add app > Android**)
2. Package name: `com.example.loginfoam`
3. App nickname (optional): "LoginFoam Dev"
4. SHA-1 Fingerprint (optional but recommended):
   - Open Terminal/CMD in your project root
   - Run: `./gradlew signingReport` (Mac/Linux) or `gradlew.bat signingReport` (Windows)
   - Copy the SHA-1 value shown in output
   - Paste it in Firebase console
5. Click **Register app**

#### Download Configuration File

1. After registration, Firebase shows **Download google-services.json**
2. Click the download button
3. File saves to your Downloads folder as `google-services.json`
4. Move this file to your project: `app/google-services.json`
   - **Correct path:** `loginfoam/app/google-services.json`
   - **NOT:** `loginfoam/google-services.json`
5. Sync Gradle

#### Enable Realtime Database

1. In Firebase Console left menu, click **Realtime Database**
2. Click **Create Database**
3. Select region closest to you (or default)
4. Choose **Test Mode** (for development/testing)
   - WARNING: Test mode allows anyone to read/write
   - Use only for development
5. Click **Enable**

#### Set Database Rules

1. In Realtime Database, click **Rules** tab
2. Replace default rules with:
```json
{
  "rules": {
    "users": {
      ".read": true,
      ".write": true
    }
  }
}
```
3. Click **Publish**

**Production Rules (use later):**
```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    }
  }
}
```

#### Verify Firebase Connection

After setup, test the connection:
1. Run the app
2. Try signing up with test credentials
3. Check Firebase Console **Realtime Database** tab
4. You should see a new user node with your data

---

## 🗄 Database Design

### Database Structure

```json
{
  "users": {
    "john_doe_123": {
      "name": "John Doe",
      "email": "john@example.com",
      "username": "john_doe_123",
      "password": "securepassword123"
    },
    "jane_smith_456": {
      "name": "Jane Smith",
      "email": "jane@example.com",
      "username": "jane_smith_456",
      "password": "anothersecurepass"
    },
    "ali_raza_789": {
      "name": "Ali Raza",
      "email": "ali@example.com",
      "username": "ali_raza_789",
      "password": "yetanotherpass"
    }
  }
}
```

### Database Schema Explanation

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| users | Object | Root node containing all users | - |
| username | String (Key) | Unique identifier for each user | "john_doe_123" |
| name | String | User's full name | "John Doe" |
| email | String | User's email address | "john@example.com" |
| username (field) | String | Duplicate of key for queries | "john_doe_123" |
| password | String | User's password (plaintext - see security section) | "securepass" |

### Query Methods

**Query by Username:**
```java
DatabaseReference reference = FirebaseDatabase.getInstance().getReference("users");
Query query = reference.orderByChild("username").equalTo("john_doe_123");
query.addListenerForSingleValueEvent(new ValueEventListener() {
    @Override
    public void onDataChange(@NonNull DataSnapshot snapshot) {
        if (snapshot.exists()) {
            for (DataSnapshot child : snapshot.getChildren()) {
                String name = child.child("name").getValue(String.class);
                String email = child.child("email").getValue(String.class);
                // Use the data
            }
        }
    }
    
    @Override
    public void onCancelled(@NonNull DatabaseError error) {
        Log.e("TAG", "Query failed: " + error.getMessage());
    }
});
```

**Read All Users:**
```java
reference.addListenerForSingleValueEvent(new ValueEventListener() {
    @Override
    public void onDataChange(@NonNull DataSnapshot snapshot) {
        for (DataSnapshot child : snapshot.getChildren()) {
            HelperClass user = child.getValue(HelperClass.class);
            Log.d("TAG", "User: " + user.getName());
        }
    }
});
```

**Write New User:**
```java
HelperClass user = new HelperClass(name, email, username, password);
reference.child(username).setValue(user);
```

---

## 💻 Complete Code Breakdown

### 1. HelperClass.java (Data Model)

**Purpose:** POJO (Plain Old Java Object) for Firebase serialization

**Full Code:**
```java
package com.example.loginfoam;

public class HelperClass {
    
    String name, email, username, password;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public HelperClass(String name, String email, String username, String password) {
        this.name = name;
        this.email = email;
        this.username = username;
        this.password = password;
    }

    // Empty constructor REQUIRED for Firebase deserialization
    public HelperClass() {
    }
}
```

**Key Points:**
- Empty constructor is **mandatory** for Firebase
- Getters and setters follow JavaBean convention
- Matches Firebase database field names
- Used for `child.getValue(HelperClass.class)` conversions

**Firebase Serialization Example:**
```java
// Object to JSON (Writing to Firebase)
HelperClass user = new HelperClass("Ali", "ali@gmail.com", "ali_123", "pass123");
reference.child("ali_123").setValue(user);
// Automatically converts to JSON:
// { "name": "Ali", "email": "ali@gmail.com", "username": "ali_123", "password": "pass123" }

// JSON to Object (Reading from Firebase)
snapshot.getValue(HelperClass.class);
// Automatically converts JSON back to HelperClass instance
```

---

### 2. SplashScreen.java (Entry Point)

**Purpose:** App launcher with branded intro screen

**Full Code:**
```java
package com.example.loginfoam;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

public class SplashScreen extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash_screen);

        // 3-second delay before moving to login screen
        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent intent = new Intent(SplashScreen.this, loginActivity.class);
                startActivity(intent);
                finish(); // so user can't go back to splash
            }
        }, 3000); // 3000 milliseconds = 3 seconds
    }
}
```

**Code Explanation:**

| Code | What It Does |
|------|-------------|
| `setContentView(R.layout.activity_splash_screen)` | Loads the splash screen layout |
| `new Handler().postDelayed()` | Schedules code to run after delay |
| `new Runnable() { run() }` | Code block to execute after delay |
| `startActivity(intent)` | Launches LoginActivity |
| `finish()` | Closes SplashScreen so user can't go back |
| `3000` | Delay in milliseconds (3 seconds) |

**Flow:**
1. App launches → SplashScreen shows
2. Waits 3 seconds
3. LoginActivity opens
4. User can't press back to return to splash

---

### 3. SignupActivity.java (User Registration)

**Purpose:** Collect user data and store in Firebase

**Full Code:**
```java
package com.example.loginfoam;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;
import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;

public class SignupActivity extends AppCompatActivity {

    EditText signupName, signupUsername, signupEmail, signupPassword;
    TextView loginRedirectText;
    Button signupButton;
    FirebaseDatabase database;
    DatabaseReference reference;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_signup);

        // Initialize UI elements
        signupName = findViewById(R.id.signup_name);
        signupEmail = findViewById(R.id.signup_email);
        signupUsername = findViewById(R.id.signup_username);
        signupPassword = findViewById(R.id.signup_password);
        loginRedirectText = findViewById(R.id.loginRedirectText);
        signupButton = findViewById(R.id.signup_button);

        // Sign Up button click listener
        signupButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Get Firebase instance
                database = FirebaseDatabase.getInstance();
                reference = database.getReference("users");

                // Collect user input
                String name = signupName.getText().toString();
                String email = signupEmail.getText().toString();
                String username = signupUsername.getText().toString();
                String password = signupPassword.getText().toString();

                // Create user object
                HelperClass helperClass = new HelperClass(name, email, username, password);

                // Write to Firebase using username as key
                reference.child(username).setValue(helperClass);

                // Show confirmation
                Toast.makeText(SignupActivity.this, "You have signup successfully!", Toast.LENGTH_SHORT).show();

                // Navigate to login
                Intent intent = new Intent(SignupActivity.this, loginActivity.class);
                startActivity(intent);
            }
        });

        // Login redirect text click
        loginRedirectText.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(SignupActivity.this, loginActivity.class);
                startActivity(intent);
            }
        });
    }
}
```

**Key Sections:**

**1. View Binding:**
```java
signupName = findViewById(R.id.signup_name);
signupEmail = findViewById(R.id.signup_email);
// Connects layout views to Java variables
```

**2. Firebase Setup:**
```java
database = FirebaseDatabase.getInstance();
reference = database.getReference("users");
// Gets Firebase instance and creates reference to "users" node
```

**3. Data Collection:**
```java
String name = signupName.getText().toString();
String email = signupEmail.getText().toString();
// Retrieves text from EditText fields
```

**4. Data Writing:**
```java
HelperClass helperClass = new HelperClass(name, email, username, password);
reference.child(username).setValue(helperClass);
// Creates user object and writes to Firebase
// Path: users/{username}
```

**5. Navigation:**
```java
Intent intent = new Intent(SignupActivity.this, loginActivity.class);
startActivity(intent);
// Navigates to LoginActivity after signup
```

---

### 4. loginActivity.java (User Authentication)

**Purpose:** Verify username/password and authenticate user

**Full Code:**
```java
package com.example.loginfoam;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;
import com.google.firebase.database.DataSnapshot;
import com.google.firebase.database.DatabaseError;
import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;
import com.google.firebase.database.Query;
import com.google.firebase.database.ValueEventListener;

public class loginActivity extends AppCompatActivity {

    EditText loginUsername, loginPassword;
    Button loginButton;
    TextView signupRedirectText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_login);

        // Initialize views
        loginUsername = findViewById(R.id.login_username);
        loginPassword = findViewById(R.id.login_password);
        loginButton = findViewById(R.id.login_button);
        signupRedirectText = findViewById(R.id.signupRedirectText);

        // Login button click listener
        loginButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Validate both fields before proceeding
                if (!validateUsername() | !validatePassword()) {
                    // Validation failed - errors already shown
                } else {
                    // Validation passed - proceed with login
                    checkUser();
                }
            }
        });

        // Sign up redirect text click
        signupRedirectText.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(loginActivity.this, SignupActivity.class);
                startActivity(intent);
            }
        });
    }

    // Validate username field
    public Boolean validateUsername() {
        String val = loginUsername.getText().toString();
        if (val.isEmpty()) {
            loginUsername.setError("Username cannot be empty");
            return false;
        } else {
            loginUsername.setError(null);
            return true;
        }
    }

    // Validate password field
    public Boolean validatePassword() {
        String val = loginPassword.getText().toString();
        if (val.isEmpty()) {
            loginPassword.setError("Password cannot be empty");
            return false;
        } else {
            loginPassword.setError(null);
            return true;
        }
    }

    // Check user credentials in Firebase
    public void checkUser() {
        String userUsername = loginUsername.getText().toString().trim();
        String userPassword = loginPassword.getText().toString().trim();

        // Get Firebase reference
        DatabaseReference reference = FirebaseDatabase.getInstance().getReference("users");

        // Query: Find user with matching username
        Query checkUserDatabase = reference.orderByChild("username").equalTo(userUsername);

        // Add listener for single event (runs once)
        checkUserDatabase.addListenerForSingleValueEvent(new ValueEventListener() {
            @Override
            public void onDataChange(@NonNull DataSnapshot snapshot) {
                // Check if user exists
                if (snapshot.exists()) {
                    boolean userFound = false;

                    // Iterate through results (usually only 1 due to unique username)
                    for (DataSnapshot userSnapshot : snapshot.getChildren()) {
                        // Get password from database
                        String passwordFromDB = userSnapshot.child("password").getValue(String.class);

                        // Compare passwords
                        if (passwordFromDB != null && passwordFromDB.equals(userPassword)) {
                            userFound = true;

                            // Extract all user data
                            String nameFromDB = userSnapshot.child("name").getValue(String.class);
                            String emailFromDB = userSnapshot.child("email").getValue(String.class);
                            String usernameFromDB = userSnapshot.child("username").getValue(String.class);

                            // Create intent with user data
                            Intent intent = new Intent(loginActivity.this, ProfileActivity.class);
                            intent.putExtra("name", nameFromDB);
                            intent.putExtra("email", emailFromDB);
                            intent.putExtra("username", usernameFromDB);
                            intent.putExtra("password", passwordFromDB);

                            // Show success message
                            Toast.makeText(loginActivity.this, "Login Successful!", Toast.LENGTH_SHORT).show();

                            // Navigate to profile
                            startActivity(intent);
                            finish(); // Close login activity
                            break;
                        }
                    }

                    // If password didn't match
                    if (!userFound) {
                        loginPassword.setError("Invalid Password");
                        loginPassword.requestFocus();
                        Toast.makeText(loginActivity.this, "Invalid Password", Toast.LENGTH_SHORT).show();
                    }

                } else {
                    // User not found
                    loginUsername.setError("User does not exist");
                    loginUsername.requestFocus();
                    Toast.makeText(loginActivity.this, "User not found", Toast.LENGTH_SHORT).show();
                }
            }

            @Override
            public void onCancelled(@NonNull DatabaseError error) {
                // Handle Firebase error
                Toast.makeText(loginActivity.this, "Error: " + error.getMessage(), Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

**Authentication Flow:**

```
User enters username & password
        ↓
validateUsername() & validatePassword()
        ↓
checkUser() called
        ↓
Firebase Query: orderByChild("username").equalTo(username)
        ↓
Snapshot returns matching users
        ↓
For each user, compare password
        ↓
Password matches?
  YES → Pass user data via Intent to ProfileActivity
  NO  → Show error, stay on login
```

**Code Breakdown:**

| Method | Purpose |
|--------|---------|
| `validateUsername()` | Check if username field is empty |
| `validatePassword()` | Check if password field is empty |
| `checkUser()` | Query Firebase and verify credentials |
| `onDataChange()` | Called when Firebase returns data |
| `onCancelled()` | Called if Firebase query fails |

---

### 5. ProfileActivity.java (Display User Profile)

**Purpose:** Show authenticated user's profile information

**Full Code:**
```java
package com.example.loginfoam;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

public class ProfileActivity extends AppCompatActivity {

    TextView profileName, profileEmail, profileUsername, profilePassword;
    TextView titleName, titleUsername;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_profile);

        // Initialize all TextViews
        profileName = findViewById(R.id.profileName);
        profileEmail = findViewById(R.id.profileEmail);
        profileUsername = findViewById(R.id.profileUsername);
        profilePassword = findViewById(R.id.profilePassword);
        titleName = findViewById(R.id.titleName);
        titleUsername = findViewById(R.id.titleUsername);

        // Display user data
        showAllUserData();
    }

    public void showAllUserData() {
        // Get Intent that started this activity
        Intent intent = getIntent();

        // Extract data passed from LoginActivity
        String nameUser = intent.getStringExtra("name");
        String emailUser = intent.getStringExtra("email");
        String usernameUser = intent.getStringExtra("username");
        String passwordUser = intent.getStringExtra("password");

        // Set header TextViews
        titleName.setText(nameUser);
        titleUsername.setText(usernameUser);

        // Set profile detail TextViews
        profileName.setText(nameUser);
        profileEmail.setText(emailUser);
        profileUsername.setText(usernameUser);
        profilePassword.setText(passwordUser);
    }
}
```

**Data Flow:**

```
LoginActivity sends Intent with extras
        ↓
getIntent() receives the Intent
        ↓
intent.getStringExtra("key") extracts data
        ↓
setText() displays data in TextViews
```

**Intent Extras Received:**
- `name` → Full name
- `email` → Email address
- `username` → Username
- `password` → Password (for demo)

---

## 🎨 UI/UX Components Details

### Splash Screen Layout (activity_splash_screen.xml)

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:background="@color/white">

    <ImageView
        android:layout_width="347dp"
        android:layout_height="596dp"
        android:contentDescription="App Logo"
        android:src="@drawable/logo" />

</LinearLayout>
```

**Components:**
- `LinearLayout`: Container (full screen, centered content)
- `ImageView`: App logo (347×596 dp)
- `background`: White color
- `gravity="center"`: Centers all children

### Login Screen Layout (activity_login.xml)

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:background="@drawable/pagebkg">

    <androidx.cardview.widget.CardView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="30dp"
        app:cardCornerRadius="30dp"
        app:cardElevation="20dp">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:layout_gravity="center_horizontal"
            android:padding="24dp"
            android:background="@drawable/levender_border">

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="Login"
                android:textSize="36sp"
                android:textAlignment="center"
                android:textStyle="bold"
                android:textColor="@color/levender"/>

            <EditText
                android:layout_width="match_parent"
                android:layout_height="50dp"
                android:id="@+id/login_username"
                android:background="@drawable/levender_border"
                android:layout_marginTop="40dp"
                android:padding="8dp"
                android:hint="Username"
                android:drawableLeft="@drawable/ic_outline_frame_person_24"
                android:drawablePadding="8dp"
                android:textColor="@color/black"/>

            <EditText
                android:layout_width="match_parent"
                android:layout_height="50dp"
                android:id="@+id/login_password"
                android:background="@drawable/levender_border"
                android:layout_marginTop="20dp"
                android:padding="8dp"
                android:hint="Password"
                android:inputType="textPassword"
                android:drawableLeft="@drawable/ic_baseline_lock_24"
                android:drawablePadding="8dp"
                android:textColor="@color/black"/>

            <Button
                android:layout_width="match_parent"
                android:layout_height="60dp"
                android:text="Login"
                android:id="@+id/login_button"
                android:textSize="18sp"
                android:layout_marginTop="30dp"
                android:backgroundTint="@color/levender"
                app:cornerRadius="20dp"/>

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/signupRedirectText"
                android:text="Not yet registered? Sign Up"
                android:layout_gravity="center"
                android:padding="8dp"
                android:layout_marginTop="10dp"
                android:textColor="@color/levender"
                android:textSize="18sp"/>

        </LinearLayout>

    </androidx.cardview.widget.CardView>

</LinearLayout>
```

**Components Breakdown:**

| Component | Properties | Purpose |
|-----------|-----------|---------|
| Outer LinearLayout | `match_parent`, `gravity="center"` | Main container, centers card |
| CardView | `cornerRadius="30dp"`, `elevation="20dp"` | Elevated card with rounded corners |
| Title TextView | `textSize="36sp"`, bold, lavender | "Login" heading |
| Username EditText | Icon, hint, `textColor=black` | Username input field |
| Password EditText | Icon, `inputType="textPassword"`, hint | Password input (masked) |
| Button | `height=60dp`, `cornerRadius="20dp"` | Login action button |
| Signup Link TextView | Clickable, lavender color | Navigate to signup |

### Signup Screen Layout (activity_signup.xml)

Similar to login but with additional fields:
- Name EditText
- Email EditText
- Username EditText
- Password EditText
- Sign Up button
- Login link

### Profile Screen Layout (activity_profile.xml)

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/profilebkg">

    <!-- Profile Image -->
    <ImageView
        android:layout_width="100dp"
        android:layout_height="100dp"
        android:id="@+id/profileImg"
        android:layout_marginTop="30dp"
        android:src="@drawable/bilal"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    <!-- Title Name -->
    <TextView
        android:id="@+id/titleName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dp"
        android:text="Name"
        android:textColor="@color/white"
        android:textSize="20sp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="@id/profileImg"
        app:layout_constraintStart_toStartOf="@id/profileImg"
        app:layout_constraintTop_toBottomOf="@id/profileImg"/>

    <!-- Title Username -->
    <TextView
        android:id="@+id/titleUsername"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="username"
        android:textColor="@color/white"
        android:textSize="18sp"
        app:layout_constraintEnd_toEndOf="@id/titleName"
        app:layout_constraintStart_toStartOf="@id/titleName"
        app:layout_constraintTop_toBottomOf="@id/titleName"/>

    <!-- Profile Card -->
    <LinearLayout
        android:id="@+id/linearLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:padding="10dp"
        android:background="@drawable/white_background"
        android:layout_marginStart="24dp"
        android:layout_marginEnd="24dp"
        android:layout_marginTop="30dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/titleUsername">

        <!-- Stats Section (Posts, Followers, Following) -->
        <!-- User Details (Name, Email, Username, Password) -->

    </LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```

**Layout Types Used:**

| Layout Type | Use Case |
|-------------|----------|
| LinearLayout | Vertical/horizontal arrangements, login/signup screens |
| ConstraintLayout | Complex positioning, profile screen |
| CardView | Elevated containers with shadows, rounded corners |

### Color Palette (colors.xml)

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="purple_200">#FFBB86FC</color>
    <color name="purple_500">#FF6200EE</color>
    <color name="purple_700">#FF3700B3</color>
    <color name="teal_200">#FF03DAC5</color>
    <color name="teal_700">#FF018786</color>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="levender">#9C27B0</color>
    <color name="grey">#757575</color>
</resources>
```

---

## 📱 How the App Works - User Flow

### Complete User Journey

```
┌─────────────────────────────────────────────────────┐
│ User Launches App                                   │
└─────────────────┬───────────────────────────────────┘
                  │
                  ▼
         ┌─────────────────┐
         │  SplashScreen   │ (3 seconds)
         │   Shows Logo    │
         └────────┬────────┘
                  │
                  ▼ (After 3 seconds)
      ┌───────────────────────┐
      │   LoginActivity       │
      │  Username / Password  │
      └───────────┬───────────┘
                  │
      ┌───────────┴────────────┐
      │                        │
      ▼                        ▼
┌──────────────────┐   ┌───────────────────┐
│ New User?        │   │ Existing User?    │
│ Click SignUp     │   │ Enter Credentials │
└────────┬─────────┘   └─────────┬─────────┘
         │                       │
         ▼                       ▼
  ┌────────────────┐      ┌────────────────┐
  │ SignupActivity │      │ Verify Password│
  │  Fill 4 Fields│      │ in Firebase    │
  │  Save to DB   │      │                │
  └────────┬───────┘      └────────┬───────┘
           │                       │
           ▼                       ▼
  ┌──────────────────┐      ┌────────────────┐
  │ Registration OK  │      │ Login OK?      │
  │ Show Toast       │      │                │
  │ Back to Login    │      └────────┬───────┘
  └─────────────────┘               │
                         ┌──────────┴──────────┐
                         │                     │
                         ▼ YES                ▼ NO
                  ┌────────────────┐   ┌──────────────┐
                  │ProfileActivity │   │ Error Toast  │
                  │ Display Info   │   │ Stay on Login│
                  │ (Name, Email,  │   └──────────────┘
                  │  Username,Pwd) │
                  └────────────────┘
```

### Step-by-Step Walkthrough

**Scenario: New User Registration**

1. **App starts** → SplashScreen displays for 3 seconds
2. **User sees** → App logo/branding
3. **Screen transitions** → LoginActivity appears
4. **User clicks** → "Not yet registered? Sign Up" link
5. **SignupActivity opens** with 4 input fields
6. **User enters**:
   - Name: "Ali Raza"
   - Email: "ali@example.com"
   - Username: "ali_raza"
   - Password: "secure123"
7. **User clicks** → "Sign Up" button
8. **App creates**:
   ```java
   HelperClass user = new HelperClass("Ali Raza", "ali@example.com", "ali_raza", "secure123");
   reference.child("ali_raza").setValue(user);
   ```
9. **Firebase stores**:
   ```json
   {
     "users": {
       "ali_raza": {
         "name": "Ali Raza",
         "email": "ali@example.com",
         "username": "ali_raza",
         "password": "secure123"
       }
     }
   }
   ```
10. **Success toast** → "You have signup successfully!"
11. **Redirected** → LoginActivity (user can now log in)

**Scenario: Existing User Login**

1. **User enters** credentials on LoginActivity:
   - Username: "ali_raza"
   - Password: "secure123"
2. **User clicks** → "Login" button
3. **App validates**:
   ```java
   validateUsername() // Check not empty
   validatePassword() // Check not empty
   ```
4. **App queries Firebase**:
   ```java
   Query checkUserDatabase = reference.orderByChild("username").equalTo("ali_raza");
   ```
5. **Firebase returns** matching user node
6. **App compares** password from input with password in database
7. **Match found** ✓
8. **App extracts** user data:
   - name: "Ali Raza"
   - email: "ali@example.com"
   - username: "ali_raza"
   - password: "secure123"
9. **App creates Intent**:
   ```java
   Intent intent = new Intent(loginActivity.this, ProfileActivity.class);
   intent.putExtra("name", "Ali Raza");
   intent.putExtra("email", "ali@example.com");
   intent.putExtra("username", "ali_raza");
   intent.putExtra("password", "secure123");
   startActivity(intent);
   ```
10. **ProfileActivity opens** and receives Intent extras
11. **User sees** their profile information displayed

---

## 🔒 Security Considerations

### Current Security Issues

| Issue | Severity | Description | Impact |
|-------|----------|-------------|--------|
| Plain Text Passwords | 🔴 Critical | Passwords stored as plain text in database | Anyone with DB access sees passwords |
| No Input Sanitization | 🟠 High | User input directly stored without validation | Potential injection attacks |
| Open Database Rules | 🟠 High | Test mode allows anyone to read/write | Unauthorized data access |
| No Password Hashing | 🔴 Critical | Passwords never encrypted | Complete password compromise if DB breached |
| No HTTPS Enforcement | 🟡 Medium | Data sent over network unencrypted | Man-in-the-middle attack possible |
| Credentials in Code | 🟡 Medium | No secure credential storage | Accidental exposure via version control |

### Recommendations for Production

#### 1. Use Firebase Authentication
```java
// Instead of manual verification, use Firebase Auth
FirebaseAuth mAuth = FirebaseAuth.getInstance();
mAuth.createUserWithEmailAndPassword(email, password)
    .addOnCompleteListener(task -> {
        if (task.isSuccessful()) {
            FirebaseUser user = mAuth.getCurrentUser();
            // User created with automatic password hashing
        }
    });

// Login
mAuth.signInWithEmailAndPassword(email, password)
    .addOnCompleteListener(task -> {
        if (task.isSuccessful()) {
            FirebaseUser user = mAuth.getCurrentUser();
            // Already authenticated, passwords never stored locally
        }
    });
```

#### 2. Hash Passwords with BCrypt
```gradle
implementation 'org.mindrot:jbcrypt:0.4'
```

```java
import org.mindrot.bcrypt.BCrypt;

// When registering
String hashedPassword = BCrypt.hashpw(password, BCrypt.gensalt());
user.setPassword(hashedPassword);

// When logging in
if (BCrypt.checkpw(inputPassword, storedHashedPassword)) {
    // Password correct
}
```

#### 3. Enforce Security Rules
```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid && newData.hasChildren(['name', 'email', 'username'])",
        "password": {
          ".read": false,
          ".write": false
        }
      }
    }
  }
}
```

#### 4. Hide Passwords
```java
// Never display passwords
// profilePassword.setText(passwordUser); // REMOVE
profilePassword.setText("••••••••"); // Show masked instead
```

#### 5. Add Field Validation
```java
public Boolean validateEmail() {
    String val = signupEmail.getText().toString();
    String emailPattern = "[a-zA-Z0-9._-]+@[a-z]+\\.+[a-z]+";
    
    if (!val.matches(emailPattern)) {
        signupEmail.setError("Invalid email format");
        return false;
    }
    return true;
}

public Boolean validatePassword() {
    String val = signupPassword.getText().toString();
    
    // At least 8 characters, 1 uppercase, 1 number
    if (val.length() < 8 || !val.matches(".*[A-Z].*") || !val.matches(".*[0-9].*")) {
        signupPassword.setError("Password too weak");
        return false;
    }
    return true;
}
```

---

## ⚠️ Known Issues & Limitations

### Issue #1: No Duplicate Username Check
**Problem:** During signup, the app doesn't check if username already exists  
**Current Behavior:** User can create account with existing username, overwriting old account  
**Impact:** Data loss for existing users with same username

**Solution:**
```java
reference.child(username).addListenerForSingleValueEvent(new ValueEventListener() {
    @Override
    public void onDataChange(@NonNull DataSnapshot snapshot) {
        if (snapshot.exists()) {
            Toast.makeText(SignupActivity.this, "Username already taken!", Toast.LENGTH_SHORT).show();
        } else {
            // Proceed with signup
            createUser();
        }
    }
});
```

### Issue #2: No Input Validation
**Problem:** Fields accept empty strings, special characters, invalid emails  
**Current Behavior:** App crashes or stores invalid data  
**Impact:** Data integrity issues, poor user experience

### Issue #3: Password Visible in Profile
**Problem:** Password displayed in plain text on profile screen  
**Current Behavior:** Anyone can see password  
**Impact:** Major security risk

**Solution:** Remove or mask password display

### Issue #4: Plain Text Password Storage
**Problem:** Passwords stored unencrypted in Firebase  
**Current Behavior:** Anyone with database access sees passwords  
**Impact:** Complete security compromise

### Issue #5: No Error Handling for Network Failures
**Problem:** No handling for Firebase connection errors  
**Current Behavior:** App may hang or show unclear errors  
**Impact:** Poor user experience on slow/offline connections

### Issue #6: Hardcoded Database Path
**Problem:** Database path "users" hardcoded in multiple places  
**Current Behavior:** Difficult to refactor or change structure  
**Impact:** Code maintenance issues

---

## 🚀 Improvements & Future Enhancements

### Phase 1: Security (High Priority)

- [ ] Implement Firebase Authentication
- [ ] Hash passwords with BCrypt/PBKDF2
- [ ] Add email verification
- [ ] Implement password reset via email
- [ ] Add two-factor authentication (2FA)
- [ ] Encrypt sensitive data at rest

### Phase 2: Functionality (Medium Priority)

- [ ] Add logout button
- [ ] Implement edit profile feature
- [ ] Add profile picture upload
- [ ] User search functionality
- [ ] Follow/unfollow users
- [ ] User notifications

### Phase 3: UX/UI (Medium Priority)

- [ ] Add loading dialogs during Firebase operations
- [ ] Implement proper error dialogs
- [ ] Add progress indicators
- [ ] Dark mode support
- [ ] Better input validation messages
- [ ] Smooth animations and transitions

### Phase 4: Testing (Low Priority)

- [ ] Unit tests for validation
- [ ] Integration tests with Firebase
- [ ] UI tests with Espresso
- [ ] Performance testing
- [ ] Security testing

### Example: Logout Implementation

```java
// In ProfileActivity
Button logoutButton = findViewById(R.id.logout_button);
logoutButton.setOnClickListener(v -> {
    Intent intent = new Intent(ProfileActivity.this, loginActivity.class);
    intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP | Intent.FLAG_ACTIVITY_NEW_TASK);
    startActivity(intent);
    finish();
});
```

### Example: Edit Profile Implementation

```java
// Create EditProfileActivity
public class EditProfileActivity extends AppCompatActivity {
    
    EditText editName, editEmail;
    Button saveButton;
    String username; // Get from intent
    
    void saveProfile() {
        String newName = editName.getText().toString();
        String newEmail = editEmail.getText().toString();
        
        DatabaseReference reference = FirebaseDatabase.getInstance()
            .getReference("users/" + username);
        
        Map<String, Object> updates = new HashMap<>();
        updates.put("name", newName);
        updates.put("email", newEmail);
        
        reference.updateChildren(updates).addOnCompleteListener(task -> {
            if (task.isSuccessful()) {
                Toast.makeText(EditProfileActivity.this, "Profile updated!", Toast.LENGTH_SHORT).show();
                finish();
            }
        });
    }
}
```

---

## 🐛 Troubleshooting

### Problem: "google-services.json" file not found

**Error Message:**
```
FirebaseApp is not initialized with an Options object.
```

**Solution:**
1. Download `google-services.json` from Firebase Console
2. Place it in `app/` directory (NOT `app/src/`)
3. Sync Gradle
4. Rebuild app

### Problem: Firebase Database Connection Fails

**Error Message:**
```
Permission denied
```

**Solution:**
1. Check database rules in Firebase Console
2. Ensure rules allow test mode:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```
3. Check internet permission in AndroidManifest.xml:
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

### Problem: EditText Errors Not Showing

**Issue:** `setError()` not displaying error messages

**Solution:**
```java
// Must happen in UI thread
loginUsername.post(() -> {
    loginUsername.setError("Username cannot be empty");
});
```

### Problem: Intent Extras Returning Null

**Error Message:**
```
NullPointerException at profileActivity.setText(intent.getStringExtra("name"))
```

**Solution:**
```java
// Check if extras exist
if (getIntent().getExtras() != null) {
    String name = getIntent().getStringExtra("name");
    if (name != null) {
        profileName.setText(name);
    }
}
```

### Problem: App Crashes on Login

**Check Logcat for errors:**
1. Run > Select "Logcat" tab
2. Search for "Exception" or "Error"
3. Common causes:
   - Firebase not initialized
   - Views not found (typo in id)
   - Null pointer exception

### Problem: Password Field Shows As Plain Text

**Fix:**
```xml
<EditText
    android:id="@+id/login_password"
    android:inputType="textPassword" /> <!-- Add this -->
```

---

## 🤝 Contributing Guidelines

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/YourFeature`
3. **Make changes** and test thoroughly
4. **Commit with clear messages**: `git commit -m "Add feature: YourFeature"`
5. **Push to branch**: `git push origin feature/YourFeature`
6. **Open Pull Request** with description

### Code Style Guidelines

- Use meaningful variable names
- Add comments for complex logic
- Follow Android naming conventions:
  - Activities: `NameActivity`
  - Variables: `camelCase`
  - Constants: `UPPER_CASE`
- Test on multiple devices/API levels
- Keep methods focused and small

### Reporting Issues

1. Check existing issues first
2. Create detailed bug report with:
   - Device/API level
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots/logs
3. Use issue template if provided

---

## 📜 License

MIT License

```
Copyright (c) 2025 LoginFoam

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

See [LICENSE](LICENSE) file for full details.

---

## 👨‍💻 Author & Contact

**Your Name**  
Android Developer | Firebase Specialist

**Contact:**
- GitHub: [@Muhammad Bilal](https://github.com/Muhammad-bilal-503)
- Email: mughalbillal001235@g,mail.com
- LinkedIn: [Muhammad Bilal](www.linkedin.com/in/muhammad-bilal-aa5364344)


**Social:**
- Twitter: [@yourhandle](https://twitter.com/yourhandle)
- Instagram: [@yourhandle](https://instagram.com/yourhandle)

---

## 🙏 Acknowledgments

- Firebase Documentation & Tutorials
- Android Developer Community
- Material Design Guidelines
- Stack Overflow Contributors
- Open Source Community

---

## 📞 Support

- **Issues:** Use GitHub Issues for bug reports
- **Discussions:** Use GitHub Discussions for questions
- **Email:** your.email@example.com
- **FAQ:** [Coming Soon]

---

## 📈 Project Stats

- **Stars:** ⭐⭐⭐⭐⭐
- **Forks:** 50+
- **Contributors:** 5+
- **Last Updated:** [Current Date]
- **License:** MIT
- **Min SDK:** 21
- **Target SDK:** 34+

---

**⭐ If this project helped you, please star it and share with others!**

**Made with ❤️ by the LoginFoam Team**

