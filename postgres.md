# Step 1: Installation Steps for PostgreSQL

```bash
sudo curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/postgresql.gpg
```

> This ensures that both the `curl` command and the `gpg dearmor` command are executed with root privileges.

---

# Step 2: Continue with the Rest of the Installation

## Add the PostgreSQL APT Repository

```bash
echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
```

## Update the Package Lists

```bash
sudo apt update
```

## Install the Latest Version of PostgreSQL

```bash
sudo apt install postgresql
```

---

# Step 3: Check PostgreSQL Version from Command Line

```bash
psql --version
```
