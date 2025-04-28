# POC For PostgreSql Installation and Setup 
##  Steps for PostgreSQL
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
sudo nano /etc/postgresql/12/main/pg_hba.conf
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

