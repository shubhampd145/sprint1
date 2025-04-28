 Steps for PostgreSQL
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
