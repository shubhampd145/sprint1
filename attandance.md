#  Attendance-API Detailed Documentation

| Author  | Created on | Version | Last Edited On | Comment         | Reviewer       |
|---------|------------|---------|----------------|------------------|----------------|
| Shubham | 01-05-25   | v1      | 01-05-25       | Internal Review | Komal Jaiswal  |

---

##  Table of Contents
1. [Introduction](#introduction)
2. [Purpose](#purpose)
3. [System Requirements](#system-requirements)
4. [Pre-requisites](#pre-requisites)
   - [Build-Time Dependencies](#build-time-dependencies)
   - [Run-Time Dependencies](#run-time-dependencies)
5. [Important Ports](#important-ports)
6. [Architecture](#architecture)
7. [POC for Setup Attendance API](#poc-for-setup-attendance-api)
8. [Components](#components)
   - [PostgreSQL](#postgresql)
   - [Redis](#redis)
   - [Poetry](#poetry)
   - [Liquibase](#liquibase)
   - [Gunicorn](#gunicorn)
9. [Contacts](#contacts)
10. [References](#references)

---

##  Introduction 
Attendance REST API is a Python-based microservice responsible for all attendance-related transactions in the OT-Microservices.

---

##  Purpose 
The Attendance REST API provides a reliable, cross-platform, and scalable service to record, retrieve, and manage attendance data within the OT-Microservices ecosystem.

---

##  System Requirements

| System Requirement | Minimum Requirement    |
|--------------------|------------------------|
| **OS**             | Ubuntu                 |
| **Disk Space**     | 20 GB                  |
| **RAM**            | 4 GB                   |
| **Processor**      | Dual-core recommended  |
| **Instance Type**  | t2.small               |

---

##  Pre-requisites

### Build-Time Dependencies

| Name       | Description                                                            |
|------------|------------------------------------------------------------------------|
| **Poetry** | Python dependency management and packaging tool                        |
| **Make**   | Tool for running automated commands/scripts (Makefile)                 |
| **Liquibase** | Database change management tool (used for schema migrations)       |
| **Gunicorn** | WSGI HTTP server for running Python web applications                |

### Run-Time Dependencies

| Name         | Description                                                        |
|--------------|--------------------------------------------------------------------|
| **PostgreSQL** | Relational database used to store attendance data                |
| **Redis**      | In-memory store for caching and session management               |
| **Swagger**    | API documentation tool for interactive REST interface            |

---

##  Important Ports

| Inbound Traffic | Description            |
|------------------|------------------------|
| 6379             | Redis                  |
| 5432             | PostgreSQL             |
| 8080             | Gunicorn (API service) |
| 22               | SSH                    |
| 80               | External web access    |

---

##  Architecture

![image](https://github.com/user-attachments/assets/00ef17c0-ae63-4a65-8646-d98989d65b44)

---

##  POC for Setup Attendance API

📌 [Click here for Setup and Run the App for POC](https://github.com/Cloud-NInja-snaatak/Documentation/blob/Shrey-SCRUM-70/ot_ms_understanding/application/attendance/setup.md)

---

##  Components

###  PostgreSQL
PostgreSQL is a powerful, open-source object-relational database system. It is used in the Attendance API to store attendance records, user metadata, and other transactional data.

###  Redis
Redis is used as an in-memory key-value store, supporting caching and temporary session storage. It improves performance by reducing database load and enabling quick access to frequently used data.

###  Poetry
Poetry is a dependency and packaging tool for Python. It manages libraries and versions, simplifying development and deployment processes for the microservice.

###  Liquibase
Liquibase helps manage database schema changes across environments. It's used to version-control and apply database migrations in a structured and automated way.

###  Gunicorn
Gunicorn is a production-grade WSGI server that serves the Python Flask (or FastAPI) application. It handles incoming HTTP requests and serves the API endpoints efficiently.

---

##  Contacts
| Name | Email Address |
|------|---------------|
| Shubham Prasad | [shubham.prasad.snaatak@mygurukulam.co](mailto:shubham.prasad.snaatak@mygurukulam.co) |

---

## 📚 References
- [Ansible Role Documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)
- [Poetry Official Docs](https://python-poetry.org/docs/)
- [Liquibase Docs](https://www.liquibase.org/documentation/index.html)
- [Gunicorn Docs](https://docs.gunicorn.org/)
- [Redis Official Site](https://redis.io/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
