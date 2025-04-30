# POC For PostgreSql Installation and Setup 


| Author  | Created on | Version   | Last Edited On | Comment  | Reviewer |
|---------|------------|-----------|----------------|-------------------|---------------|
| Shubham | 29-04-25   |  v1| 29-04-25        | Internal Review    | Komal Jaiswal|
| Shubham | 29-04-25   | v1 | 29-04-25        | L0 Review    | Gaurav Singla|
| Shubham | 29-04-25   | v1 | 29-04-25        | L1 Review    | Rahul Gupta |
| Shubham | 29-04-25   | v1  |29-04-25        | L2 Review    | Mahesh Kumar |

## Table of Contents
- [Steps for PostgreSQL Installation](#steps-for-postgresql-installation)
  - [Step 1: Import the PostgreSQL Signing Key](#step1--import-the-postgresql-signing-key)
  - [Step 2: Add the PostgreSQL APT Repository](#step-2-add-the-postgresql-apt-repository)
  - [Step 3: Update the Package Lists](#step-3-update-the-package-lists)
  - [Step 4: Install the Latest Version of PostgreSQL](#step-4-install-the-latest-version-of-postgresql)
  - [Step 5: Check PostgreSQL Version from Command Line](#step-5-check-postgresql-version-from-command-line)
- [PostgreSQL User, Database, and Table Setup](#postgresql-user-database-and-table-setup)
  - [1. Add a New User](#1-add-a-new-user)
  - [2. Create a Database](#2-create-a-database)
  - [3. Grant Permissions to the User on the Database](#3-grant-permissions-to-the-user-on-the-database)
  - [4. Create a Table in the Database](#4-create-a-table-in-the-database)
  - [5. Insert Data into the Table](#5-insert-data-into-the-table)
  - [6. View the Data](#6-view-the-data)
  - [7. Exit `psql`](#7-exit-psql)
- [PostgreSQL Configuration: Enable Password Authentication for Users](#postgresql-configuration-enable-password-authentication-for-users)
  - [1. Edit `pg_hba.conf` File](#1-edit-pg_hbaconf-file)
  - [2. Add Authentication Method](#2-add-authentication-method)
  - [3. Restart PostgreSQL Service](#3-restart-postgresql-service)
  - [4. Connect to Database as the New User (Optional)](#4-connect-to-database-as-the-new-user-optional)
 
- [Contacts](#Contacts)
- [References](#References)

---
##  Steps for PostgreSQL Installation 
### step1 : Import the PostgreSQL signing key
```bash
sudo curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/postgresql.gpg
```


### Step 2: Add the PostgreSQL APT Repository

```bash
echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
```

### step 3: Update the Package Lists

```bash
sudo apt update
```

### step 4: Install the Latest Version of PostgreSQL

```bash
sudo apt install postgresql
```

---

### Step 5: Check PostgreSQL Version from Command Line

```bash
psql --version
```
# PostgreSQL User, Database, and Table Setup

## 1. Add a New User
First, log in to PostgreSQL as the `postgres` user:

```bash
sudo -u postgres psql
```

Inside the `psql` shell, create a new user:

```sql
CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypassword';
```
> This creates a new user called `myuser` with the password `mypassword`.

---

## 2. Create a Database
Still in the `psql` shell, create a database:

```sql
CREATE DATABASE mydb;
```

---

## 3. Grant Permissions to the User on the Database
Grant the new user (`myuser`) all privileges on the newly created database (`mydb`):

```sql
GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;
ALTER USER myuser WITH SUPERUSER;
```

---

## 4. Create a Table in the Database
Now, connect to the `mydb` database:

```sql
\c mydb
```

After connecting, create a table:

```sql
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    position VARCHAR(100),
    salary NUMERIC
);
```

---

## 5. Insert Data into the Table
Insert some sample data into the `employees` table:

```sql
INSERT INTO employees (name, position, salary) 
VALUES 
    ('Alice', 'Engineer', 60000),
    ('Bob', 'Manager', 80000);
```

---

## 6. View the Data
You can view the data inserted into the table with the following query:

```sql
SELECT * FROM employees;
```

---

## 7. Exit `psql`
To exit the `psql` prompt:

```sql
\q
```

# PostgreSQL Configuration: Enable Password Authentication for Users

## 1. Edit `pg_hba.conf` File
Open the PostgreSQL Host-Based Authentication configuration file:

```bash
sudo nano /etc/postgresql/17/main/pg_hba.conf
```

---

## 2. Add Authentication Method

```
local   all             myuser                                md5
```

---

## 3. Restart PostgreSQL Service
After saving changes to `pg_hba.conf`, restart the PostgreSQL service to apply the changes:

```bash
sudo systemctl restart postgresql
```

---

## 4. Connect to Database as the New User (Optional)
Now, you can connect to the database as `myuser`:

```bash
psql -U myuser -d mydb -W
```
- `-U myuser`: Connect as the `myuser`.
- `-d mydb`: Connect to the `mydb` database.
- `-W`: Force `psql` to prompt for the password.


##  Contacts
| Name | Email Address |
|------|---------------|
| Shubham Prasad | [shubham.prasad.snaatak@mygurukulam.co](mailto:shubham.prasad.snaatak@mygurukulam.co) |

##  References
| Links | Descriptions |
|-------|--------------|
| [DigitalOcean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-20-04) | Postgresql   installation step by step|

