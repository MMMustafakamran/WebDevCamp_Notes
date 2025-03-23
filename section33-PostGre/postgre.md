# **PostgreSQL Notes**

## **Introduction to PostgreSQL**

- PostgreSQL (or Postgres) is a powerful, open-source relational database management system (RDBMS).
- Used by major companies like Apple, Twitch, Instagram, and NASA.
- Known as *"The World's Most Advanced Open Source Relational Database."*
- Free to use and has strong community support.

### **Why Use PostgreSQL?**

✅ Industry Standard – Widely used by companies.
 ✅ Open Source – No licensing costs.
 ✅ Strong Community – Lots of support and documentation.
 ✅ Career Growth – Used in many industries.

------

## **How PostgreSQL Works in a Web App**

### **Basic Architecture:**

1. **Client (Frontend)** – User interacts with the web app.
2. **Server (Backend)** – Handles requests, processes logic, and communicates with the database.
3. **PostgreSQL Database** – Stores data (e.g., users, posts, transactions).

- The backend (e.g., using Node.js) connects to PostgreSQL to **store and retrieve data**.
- PostgreSQL can be hosted **locally** or on a **remote server/cloud**.

------

## **Setting Up PostgreSQL with Node.js**

### **Installing Required Software:**

1. **PostgreSQL Server** – Runs the database locally.
2. **pgAdmin** – A GUI tool for managing the database (alternative to using the command line).

### **Connecting Node.js to PostgreSQL**

- Use the **pg** package (node-postgres) to interact with the database.

#### **Example: Connecting to PostgreSQL in Node.js**

```javascript
const { Client } = require("pg");

const db = new Client({
  user: "your_username",
  host: "localhost",
  database: "your_database",
  password: "your_password",
  port: 5432, // Default PostgreSQL port
});

db.connect();

db.query("SELECT * FROM users;", (err, res) => {
  if (err) {
    console.error(err);
  } else {
    console.log(res.rows);
  }
  db.end();
});
```

**Key Points:**

- `db.query()` is used to execute SQL queries.
- The connection must be closed using `db.end()`.

------

## **Creating Tables in PostgreSQL**

- **Tables** consist of **columns (fields)** and **rows (records)**.
- Each column has a specific **data type** (e.g., `VARCHAR`, `INT`, `BOOLEAN`).

#### **Example: Creating a Table in SQL**

```sql
CREATE TABLE friends (
  id SERIAL PRIMARY KEY,  -- Auto-incrementing unique identifier
  name VARCHAR(50),       -- Stores names, max length 50 characters
  age INT,                -- Stores age as an integer
  is_cool BOOLEAN         -- True or False
);
```

### **Understanding Data Types:**

| Data Type    | Description                                 |
| ------------ | ------------------------------------------- |
| `SERIAL`     | Auto-increments, used for primary keys      |
| `VARCHAR(n)` | Variable-length string (max `n` characters) |
| `TEXT`       | Unlimited-length text                       |
| `INT`        | Whole numbers                               |
| `BOOLEAN`    | True/False values                           |
| `DATE`       | Stores dates                                |

🔹 *Use `VARCHAR(n)` for efficient storage, but `TEXT` if you need flexibility.*
 🔹 *`SERIAL` automatically assigns a unique ID to each new row.*

------

## **Retrieving Data with Queries**

- PostgreSQL uses **SQL** (Structured Query Language) to interact with data.

#### **Example Queries:**

**Get all users:**

```sql
SELECT * FROM users;
```

**Get users older than 18:**

```sql
SELECT * FROM users WHERE age > 18;
```

**Update a record:**

```sql
UPDATE users SET is_cool = TRUE WHERE name = 'Jack';
```

**Delete a user:**

```sql
DELETE FROM users WHERE id = 3;
```

------

## **Conclusion**

- PostgreSQL is a **powerful**, **widely-used**, and **free** database system.
- Works well with **Node.js** using the `pg` package.
- **Tables** store structured data efficiently with various **data types**.
- **SQL queries** allow fetching, updating, and deleting data.

👉 **Next Steps:** Install PostgreSQL, set up `pgAdmin`, and start practicing queries! 🚀

------

This should help you quickly reference PostgreSQL concepts. Let me know if you need anything else, you legend. 😎

Got it! Here's a properly formatted, structured set of notes based on what you provided:

------

# **PostgreSQL: Creating and Importing Data from CSV Files**

## **1. Introduction to CSV Files in PostgreSQL**

- CSV (**Comma Separated Values**) files store tabular data in plain text format.

  

------

## **2. Creating a PostgreSQL Database in pgAdmin**

### **Step 1: Open pgAdmin and Connect to PostgreSQL**

- Open **pgAdmin** and enter the **global password** if prompted.
- Expand **Servers** → **PostgreSQL 15** → Enter the **Postgres password** (set during installation).

### **Step 2: Create a New Database**

1. Expand **Databases** in the left panel.
2. Right-click on **Databases** → Click **Create Database**.
3. Name the database: `world`.
4. Owner: **postgres** (default).
5. Click **Save**.

------

## **3. Creating a Table for Capitals Data**

### **Step 1: Open Query Tool**

- In pgAdmin, **select the `world` database**.
- Click on **Query Tool** to write SQL commands.

### **Step 2: Create the `capitals` Table**

Use the following SQL command:

```sql
CREATE TABLE capitals (
  id SERIAL PRIMARY KEY,  -- Unique identifier (auto-increment)
  country VARCHAR(45),    -- Country name (max 45 characters)
  capital VARCHAR(45)     -- Capital name (max 45 characters)
);
```

✅ `SERIAL` = Auto-incrementing unique ID.
 ✅ `VARCHAR(45)` = Text field limited to 45 characters.
 ✅ `PRIMARY KEY` ensures each `id` is unique.

### **Step 3: Verify Table Creation**

- Click **Run**.
- If successful, right-click on `Tables` → **Refresh** → `capitals` table appears.
- To view the empty table:
  - Right-click `capitals` → **View/Edit Data** → **All Rows**.

------

## **4. Importing Data from capitals.csv**

### **Step 1: Start Import Process**

1. Right-click **capitals** table → Select **Import/Export Data**.

2. In the 

   Import/Export

    window:

   - **Choose Import**.
   - **Select the CSV file** (`capitals.csv`).
   - **Ensure Format is CSV**.
   - Go to **Options** → Check ✅ **Header** (first row contains column names).
   - Click **OK**.

### **Step 2: Verify Imported Data**

- Right-click **capitals** table → **Refresh**.
- View data:
  - Right-click `capitals` → **View/Edit Data** → **All Rows**.
- The table should now be populated with country and capital data.

Here are your notes with proper formatting and organization:

------

# **Building a Capitals Quiz with Node.js, Express, and PostgreSQL**

## **Overview**

We will create a Capitals Quiz powered by a PostgreSQL database. The quiz will prompt users with a country name, and they must enter the corresponding capital. The backend will verify answers, normalize input, and track scores until the user gets an answer wrong.

------

## **Setting Up the Project**

1. **Download and Extract Files:**

   - Download the **World Capital Quiz** zip file.
   - Extract the files and open the project in **VS Code**.

2. **Install Dependencies:**

   - Navigate to the project folder in the terminal.

   - Run:

     ```bash
     npm install
     ```

   - This will install all necessary Node modules.

3. **Project Structure:**

   - **index.js** → Backend logic
   - **index.ejs** → Frontend template
   - **public/** → Contains **main.css** and other static files

------

## **Understanding the Existing Code**

### **Express Server Setup**

- Runs on port **3000**
- Middleware setup:
  - `express.static('public')` → Serves static files
  - `body-parser` → Parses form data

### **Quiz Logic (Before Using Database)**

- Hardcoded quiz questions stored in an array
- Randomly selects a country and asks the user for the capital
- Compares the user input with the correct answer
  - Uses `.toLowerCase()` to normalize casing
  - Uses `.trim()` to remove extra spaces
- Tracks score until the user gets an answer wrong

------

## **Integrating PostgreSQL**

### **1. Install pg Package**

```bash
npm install pg
```

### **2. Import and Configure PostgreSQL Client**

```javascript
import pg from "pg";

const db = new pg.Client({
    user: "postgres", 
    host: "localhost", 
    database: "world", 
    password: "your_password", 
    port: 5432
});
db.connect();
```

> **Note:** Update `your_password` with your actual PostgreSQL password.

### **3. Fetch Data from Database**

Replace hardcoded quiz data with database records:

```javascript
db.query("SELECT * FROM capitals", (err, res) => {
    if (err) {
        console.log(err);
    } else {
        quiz = res.rows;
    }
    db.end();
});
```

### **4. Run the Project**

```bash
nodemon index.js
```

- Open `http://localhost:3000` in your browser.
- The game will now pull **random questions** from the database!

------

## **Exercise: Flags Quiz**

### **Objective:**

Create a new quiz where users guess the country based on a flag.

### **Steps:**

1. Download and extract **8.2 Postgres READ.zip**.

2. Install dependencies:

   ```bash
   npm install
   ```

3. Modify **index.js** to:

   - Fetch data from the `flags` table.
   - Use `"SELECT * FROM flags"` instead of `"capitals"`.
   - Ensure correct field names (`name` and `flag`).

4. Run the solution:

   ```bash
   nodemon solution.js
   ```

### **Play the Game:**

- Visit `http://localhost:3000`
- Try guessing the country based on the flag!

------

## **Final Thoughts**

- Modify the game with your own quiz topics!
- Share your highest scores.
- Experiment by creating new tables in PostgreSQL.

------

This structured guide ensures clear understanding and easy implementation. 🚀 Let me know if you need further refinements!