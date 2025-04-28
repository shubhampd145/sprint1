# PostgreSQL Proof of Concept

## Document Information

| Author      | Created on   | Version    | Last updated by | Last edited on | Reviewer      |
|-------------|--------------|------------|-----------------|----------------|---------------|
| *Pooja Bhanu* | 10-02-2025 | Version 2  | *Pooja Bhanu*  | 21-02-2025     | *Komal Jaiswal* |
| *Pooja Bhanu* | 10-02-2025 | Version  1 | *Pooja Bhanu*  | 10-02-2025     | *Komal Jaiswal* |


## Table of Contents

1. [PostgreSQL Installation on Ubuntu](#postgresql-installation-on-ubuntu)
   1. [Step 1: Update package list](#step-1-update-package-list)
   2. [Step 2: Install PostgreSQL and contrib package](#step-2-install-postgresql-and-contrib-package)
   3. [Step 3: Start PostgreSQL service](#step-3-start-postgresql-service)
   4. [Step 4: Access PostgreSQL shell](#step-4-access-postgresql-shell)
   5. [Step 5: Create a new database](#step-5-create-a-new-database)
   6. [Step 6: Configure PostgreSQL for External Connections](#step-6-configure-postgresql-for-external-connections)
   7. [Step 7: Edit pg_hba.conf](#step-7-edit-pghba-conf)
   8. [Step 8: Restart PostgreSQL to apply changes](#step-8-restart-postgresql-to-apply-changes)
2. [Contact Information](#contact-information)
 

### PostgreSQL Installation on Ubuntu

### Step 1: Update package list

bash
sudo apt-get update


   
### Step 2: Install PostgreSQL and contrib package, then check the version:

  [Click here for installation steps](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/1f2d6373cfa4e470f080396f5838cc31bf98fd44/Common/Software/PostgreSql/installation/Readme.md)

  We are using Postgresql version 16.6


### Step 3: Start PostgreSQL service

bash
sudo systemctl start postgresql


bash
sudo systemctl enable postgresql


### Step 4: Access PostgreSQL shell 

bash
sudo -u postgres psql


The command sudo -u postgres psql is used to connect to a PostgreSQL database as the postgres user, which is the default superuser in PostgreSQL.

- *sudo*: This is a command used to execute other commands with superuser privileges.

- *-u postgres*: This option tells sudo to run the command as a specific user—in this case, the postgres user. 

- *psql*: This is the command-line tool for interacting with PostgreSQL databases. It allows users to run SQL commands, query the database, and manage PostgreSQL databases directly from the command line.

### Step 5: Create a new database

[Click here to create database](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/9d429530ec0e5dfecd3486266628b4e5d0faad71/Common/Software/PostgreSql/installation/Readme.md)

bash
CREATE DATABASE Zero_Downtime_Crew;


-  *Exit PostgreSQL shell*

    \q

### Step 6: Configure PostgreSQL for External Connections

 [Click here for Configuration steps](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/64ae04c0d2a1980301c3e2d99cf60f2179597823/Common/Software/PostgreSql/configuration/Readme.md)

bash
listen_addresses = '172.31.82.140'


This is a specific configuration setting within the postgresql.conf file. It controls the network addresses that PostgreSQL will listen on for incoming connections.

*listen_addresses*: This is a configuration parameter in PostgreSQL that determines which network interfaces the PostgreSQL server should listen to for incoming connections. It defines the IP addresses on which the PostgreSQL service will accept connections.

- *172.31.82.140*: This is a specific IP address. By setting this value, PostgreSQL will only accept incoming connections from the machine with the IP address 172.31.82.140.


 ### Step 7: Edit pg_hba.conf <a name="step-7-edit-pghba-conf"></a>  


 [Click here for Configuration steps](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/64ae04c0d2a1980301c3e2d99cf60f2179597823/Common/Software/PostgreSql/configuration/Readme.md)


bash
    host    Zero_downtime_crew           pooja             172.31.82.140/24          md5


The file pg_hba.conf (PostgreSQL Host-Based Authentication file) is responsible for controlling client authentication for PostgreSQL.It defines who can connect to the PostgreSQL server, from where they can connect, and what authentication method to use.


- *host* - This specifies the type of connection. host means the connection is coming over TCP/IP, which is the standard network connection method.

- *Zero_Downtime_Crew*: This is the name of the database that this rule applies to. It means the rule applies to the Zero_downtime_crew database.

- *pooja*: This is the username. This rule applies to the user pooja.

- *172.31.82.140/24*: This specifies the client's IP address range that can connect. The /24 is a CIDR notation for the IP address range. It means any IP address in the 172.31.82.140 subnet, from 172.31.82.0 to 172.31.82.255, is allowed to connect.

- *md5* - md5 is one of the authentication methods used to verify the identity of a user attempting to connect to the database

### Step 8: Restart PostgreSQL to apply changes

bash
sudo systemctl restart postgresql


---
### Contact Information


| Name         | Email Address                     |
|--------------|-----------------------------------|
| *Pooja Bhanu* | pooja.bhanu@mygurukulam.co        |
