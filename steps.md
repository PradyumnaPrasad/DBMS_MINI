# Apartment Management System - Demo Steps

## Project Overview
This is a comprehensive Apartment Management System built as a DBMS mini-project. It allows administrators, owners, tenants, and employees to manage various aspects of an apartment complex, including user authentication, tenant/owner management, complaint tracking, maintenance payments, parking slot allocation, and room details.

The system uses a MySQL database for data storage, a Node.js/Express backend for API handling, and a React frontend for the user interface.

## Technologies Used
- **Frontend**: React.js (with React Router, Axios for API calls, Tailwind CSS for styling, Particles.js for background effects)
- **Backend**: Node.js with Express.js
- **Database**: MySQL (with MySQL2 driver)
- **Database Management**: TablePlus (GUI tool for MySQL)
- **Development Tools**: VS Code, npm, nodemon
- **Other Libraries**: bcrypt for password hashing (if implemented), CORS for cross-origin requests

## Prerequisites
- Node.js (v18 or higher recommended, but v25 works with fixes)
- MySQL Server (local installation)
- TablePlus (for database management)
- Git (for cloning the repository)
- A web browser (Chrome/Firefox recommended)

## Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/imtharun/apartment-management-system-dbms.git
cd apartment-management-system-dbms
```

### 2. Database Setup with TablePlus
1. Open **TablePlus**.
2. Create a new MySQL connection to your local MySQL server.
3. Create a new database named `app`.
4. Select the `app` database.
5. Go to **File** > **Import** > **From SQL Dump...**
6. Select the file `database/export.sql` from the project folder.
7. Click **Import** to create all tables and insert sample data.

### 3. Backend Setup
1. Navigate to the server directory:
   ```bash
   cd server
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Update database configuration in `server/config_sql.js`:
   ```javascript
   module.exports = {
       host: "localhost",
       uname: "your_mysql_username",  // e.g., "root"
       upass: "your_mysql_password",  // e.g., "password"
       database: "app"
   };
   ```

### 4. Frontend Setup
1. Navigate to the client directory:
   ```bash
   cd ../client
   ```
2. Install dependencies:
   ```bash
   npm install --legacy-peer-deps  # Use legacy peer deps to resolve React 18 + Material UI v4 conflicts
   ```

## Running the Application

### Start the Backend Server
```bash
cd server
npm start
```
- The server will run on `http://localhost:5001`
- You should see "Server starten to listen..." and "database Connected!"

### Start the Frontend Client
Open a new terminal window:
```bash
cd client
npm start
```
- The React app will run on `http://localhost:3000`
- It will automatically open in your browser

## Demo Steps

### 1. Login as Different User Types
The system supports four user types: Admin, Employee, Owner, Tenant.

**Pre-loaded User Credentials:**
- **Admin**: User ID: `a-123`, Password: `12345678`
- **Employee**: User ID: `e-123`, Password: `12345678`
- **Owner**: User ID: `o-123`, Password: `12345678`
- **Tenant**: User ID: `t-123`, Password: `12345678`

**Demo Flow:**
1. Open `http://localhost:3000` in your browser.
2. Enter User ID and Password (e.g., `a-123` and `12345678`).
3. Click "Login" - you'll be redirected to the dashboard based on your role.

### 2. Admin Dashboard Features
- **Create Owner**: Add new apartment owners.
  - Fill form: Owner ID (unique integer, e.g., 505), Name, Age, Room No (must exist: 11,12,13,21,31,67), Agreement Status (Yes/No), DOB (DD-MM-YYYY), Aadhaar, Password.
  - New owner can login with User ID `o-{owner_id}`.
- **Create Tenant**: Add new tenants (similar process).
- **Allot Parking Slot**: Assign parking slots to tenants.
- **View All Details**: See owners, tenants, rooms, etc.

### 3. Owner Dashboard Features
- **View Tenant Details**: See tenants in their rooms.
- **View Complaints**: Check complaints from tenants.
- **Room Details**: View room information.

### 4. Tenant Dashboard Features
- **Raise Complaints**: Submit maintenance issues.
- **Pay Maintenance**: Make payments (simulated).
- **View Details**: Check personal and room info.

### 5. Employee Dashboard Features
- **View Complaints**: Handle tenant complaints.
- **Manage Maintenance**: Oversee payments and issues.

## Key Features to Demonstrate

### User Management
- Role-based authentication (Admin/Employee/Owner/Tenant)
- Secure login with password validation
- User creation with proper data validation

### Apartment Management
- Room allocation and tracking
- Owner-tenant relationships
- Parking slot management

### Complaint System
- Tenants can raise complaints
- Owners and employees can view/manage complaints

### Maintenance Tracking
- Payment system for maintenance fees
- Status tracking

### Database Integrity
- Foreign key constraints ensure data consistency
- Referential integrity between tables (owner-room, tenant-room, etc.)

## Database Schema Overview
- **auth**: User authentication (user_id, password, id)
- **owner**: Owner details (owner_id, name, age, room_no, etc.)
- **tenant**: Tenant details
- **room**: Room information (room_no, type, floor, parking_slot)
- **block**: Building blocks
- **complaints**: Maintenance issues
- **identity**: Aadhaar/proof storage
- **maintenance**: Payment records

## Troubleshooting

### Common Issues
1. **Port 5000/5001 in use**: Kill the process using `lsof -i :5001` then `kill -9 <PID>`
2. **MySQL connection error**: Check credentials in `config_sql.js`
3. **React compilation error**: Ensure Node.js v18+ and use `--legacy-peer-deps`
4. **Foreign key errors**: Use existing room numbers when creating owners/tenants
5. **Login fails**: Ensure correct User ID format (starts with role letter)

### Backup Commands
- **Restart Server**: `cd server && npm start`
- **Restart Client**: `cd client && npm start`
- **Check DB Connection**: Look for "database Connected!" in server logs

## Demo Script Suggestions
1. Start with admin login and show user creation
2. Switch to owner view to demonstrate complaint viewing
3. Login as tenant to raise a complaint and make a payment
4. Show employee handling complaints
5. Demonstrate data integrity by trying invalid operations

## What You're Using
- **Database**: MySQL for relational data storage with proper normalization
- **Backend**: RESTful API with Express.js for CRUD operations
- **Frontend**: Single-page application with React for responsive UI
- **Styling**: Tailwind CSS for modern design
- **State Management**: React hooks and context
- **Authentication**: Session-based with role-based access control
- **Deployment Ready**: Modular structure for easy scaling

This system demonstrates real-world apartment management with proper database design, user roles, and full-stack development practices.</content>
<parameter name="filePath">/Users/pradyumnaprasad/Desktop/DBMSmini/apartment-management-system-dbms/steps.md