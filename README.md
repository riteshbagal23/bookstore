# How to Run Bookstore Application on Windows

## Prerequisites
https://chatgpt.com/share/692b3483-3ca0-800f-aa1f-d6f580456d63

Before starting, ensure you have the following installed on your Windows machine:

1. **Node.js and npm** - Download from https://nodejs.org/ (LTS version recommended)
2. **MySQL Server** - Download from https://dev.mysql.com/downloads/mysql/
3. **Git** (optional) - For cloning the repository

Verify installations by opening Command Prompt (cmd) or PowerShell and running:
```cmd
node --version
npm --version
mysql --version
```

## Setup Steps

### Step 1: Extract/Clone the Project

Navigate to where you want to store the project:
```cmd
cd Desktop
```

If you have the project as a zip file, extract it. Otherwise, clone it using git:
```cmd
git clone <repository-url>
cd bookstore
```

### Step 2: Setup Database (MySQL)

1. **Start MySQL Server**
   - Open MySQL Command Line Client or use MySQL Workbench
   - Log in with your MySQL credentials (default: root/root)

2. **Create Database and Tables**
   ```sql
   CREATE DATABASE bookstore;
   USE bookstore;

   CREATE TABLE users (
     id INT AUTO_INCREMENT PRIMARY KEY,
     name VARCHAR(255) NOT NULL,
     email VARCHAR(255) UNIQUE NOT NULL,
     password VARCHAR(255) NOT NULL,
     created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   CREATE TABLE books (
     id INT AUTO_INCREMENT PRIMARY KEY,
     title VARCHAR(255) NOT NULL,
     author VARCHAR(255) NOT NULL,
     price DECIMAL(10, 2) NOT NULL,
     description TEXT,
     created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

3. **Update Backend Database Configuration**
   - Open `backend/db.js` in a text editor
   - Verify or update the MySQL connection details:
   ```javascript
   const connection = mysql.createConnection({
     host: 'localhost',
     user: 'root',        // Your MySQL username
     password: 'root',    // Your MySQL password
     database: 'bookstore'
   });
   ```

### Step 3: Setup Backend

1. **Open Command Prompt/PowerShell**

2. **Navigate to Backend Directory**
   ```cmd
   cd bookstore\backend
   ```

3. **Install Dependencies**
   ```cmd
   npm install
   ```

4. **Start Backend Server**
   ```cmd
   npm start
   ```
   or
   ```cmd
   node server.js
   ```

   You should see: `Server running on port 5000`

### Step 4: Setup Frontend

1. **Open Another Command Prompt/PowerShell Window**

2. **Navigate to Frontend Directory**
   ```cmd
   cd bookstore\frontend
   ```

3. **Install Dependencies**
   ```cmd
   npm install
   ```

4. **Start Frontend Development Server**
   ```cmd
   npm start
   ```

   This will automatically open your browser at `http://localhost:3000`

## Troubleshooting

### Port Already in Use

If you get "EADDRINUSE: address already in use :::5000" error:

1. **Find the process using port 5000**
   ```cmd
   netstat -ano | findstr :5000
   ```

2. **Kill the process** (replace PID with the actual process ID)
   ```cmd
   taskkill /PID <PID> /F
   ```

### npm command not found

- Ensure Node.js is installed correctly
- Restart Command Prompt after installing Node.js
- Check if npm is in your PATH: `npm --version`

### MySQL Connection Error

- Ensure MySQL Server is running
- Verify username and password in `backend/db.js`
- Check if port 3306 is open
- Ensure the `bookstore` database exists

### "Module not found" errors

In both frontend and backend directories, run:
```cmd
npm install
```

### White screen on frontend

- Check browser console (F12) for errors
- Ensure backend server is running on port 5000
- Check that `frontend/src/api.js` has correct backend URL

## Running the Application

Once everything is set up:

1. **Terminal 1 - Start MySQL Server** (if not already running)
   ```cmd
   mysql -u root -p
   ```

2. **Terminal 2 - Start Backend**
   ```cmd
   cd bookstore\backend
   npm start
   ```
   Runs on: `http://localhost:5000`

3. **Terminal 3 - Start Frontend**
   ```cmd
   cd bookstore\frontend
   npm start
   ```
   Runs on: `http://localhost:3000`

## Accessing the Application

Open your browser and go to:
```
http://localhost:3000
```

### Available Pages
- **Home** - Welcome page
- **Catalogue** - List of books
- **Login** - User login
- **Register** - User registration

## Stopping the Application

To stop any server, press `Ctrl + C` in the Command Prompt/PowerShell window

## Additional Notes

- Backend runs on **port 5000**
- Frontend runs on **port 3000**
- MySQL server typically runs on **port 3306**
- Make sure all three are running for the full application to work

## Contact & Support

For issues or questions, please contact the development team or check the project documentation. i want to add this file in 
