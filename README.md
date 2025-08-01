VitalTracker Pro - Local Setup Guide for Visual Studio Code
This guide will help you run VitalTracker Pro on your local machine using Visual Studio Code.

Step 1: Prerequisites
Before starting, make sure you have:

Required Software
Node.js (version 18 or higher)

Download from: https://nodejs.org/
Choose the LTS version
Verify installation: Open terminal and run node --version
Visual Studio Code

Download from: https://code.visualstudio.com/
Git (if not already installed)

Download from: https://git-scm.com/
Step 2: Open Project in Visual Studio Code
Open Visual Studio Code
Click "File" → "Open Folder"
Select the VitalTracker Pro folder you downloaded
Click "Select Folder"
Step 3: Install Dependencies
Open the terminal in VS Code:

Press `Ctrl + `` (backtick) or go to "Terminal" → "New Terminal"
Install all required packages:

npm install
Wait for installation to complete (this may take 2-3 minutes)

Step 4: Set Up Database
You have two options for the database:

Option A: Use Neon (Cloud Database - Recommended)
Go to https://neon.tech and create a free account
Create a new project
Copy the connection string (it looks like: postgresql://username:password@host/database)
Option B: Use Local PostgreSQL
Install PostgreSQL on your computer
Create a new database
Note your connection details
Step 5: Create Environment File
In VS Code, create a new file called .env in the root folder (same level as package.json)
Add the following content (replace the values with your actual database details):
# Database Configuration
DATABASE_URL=postgresql://username:password@host:5432/database_name
PGHOST=your_database_host
PGPORT=5432
PGUSER=your_username
PGPASSWORD=your_password
PGDATABASE=your_database_name
# Session Security (generate a random string)
SESSION_SECRET=your_random_secret_key_here_make_it_long_and_random
# Authentication Mode
USE_LOCAL_AUTH=true
NODE_ENV=development
Important Notes:
Replace your_database_host, your_username, your_password, etc. with your actual database details
For SESSION_SECRET, use a long random string (you can generate one online or just type random characters)
If using Neon, you only need the DATABASE_URL - the other PG* variables will be extracted automatically
Step 6: Set Up Database Tables
Run this command in the terminal:

npm run db:push
This will create all the necessary tables in your database.

Step 7: Start the Application
Run this command:

npm run dev
You should see output like:

> rest-express@1.0.0 dev
> NODE_ENV=development tsx server/index.ts
[express] serving on port 5000
Step 8: Open the Application
Open your web browser
Go to: http://localhost:5000
You should see the VitalTracker Pro landing page
Step 9: Create Your Account
Click "Start Tracking Today" button
Click on the "Sign Up" tab
Fill in your details:
First Name and Last Name
Email address
Password
Click "Create Account"
You'll be automatically logged in and taken to the dashboard
Troubleshooting
If you get "npm: command not found"
Node.js is not installed properly
Restart your computer after installing Node.js
If you get database connection errors
Check your .env file has the correct database details
Make sure your database is running (if using local PostgreSQL)
Verify the DATABASE_URL format is correct
If the page won't load
Make sure you're going to http://localhost:5000 (not https)
Check that port 5000 isn't being used by another application
Look at the terminal for any error messages
If authentication doesn't work
Make sure USE_LOCAL_AUTH=true is in your .env file
Verify SESSION_SECRET is set in your .env file
What You Can Do
Once the application is running, you can:

Track vital signs (heart rate, blood pressure, temperature, etc.)
Manage medications and doses
Schedule appointments with doctors
View health reports and charts
Set health goals
Manage emergency contacts
Getting Help
If you encounter any issues:

Check the terminal for error messages
Make sure all steps were followed correctly
Verify your .env file is properly configured
Try restarting the application with npm run dev
Stopping the Application
To stop the application:

Press Ctrl + C in the terminal
Or close the terminal window
Next Time
To run the application again:

Open the project folder in VS Code
Open terminal
Run npm run dev
Go to http://localhost:5000
The application is now fully portable and will work on any computer with Node.js installed!
