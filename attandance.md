# Attandence-Api Detailed Documentation 

| Author  | Created on | Version   | Last Edited On | Comment  | Reviewer |
|---------|------------|-----------|----------------|-------------------|---------------|
| Shubham | 01-05-25   |  v1    | 01-05-25       | Internal Review     | Komal Jaiswal|


## Introduction 
Attendance REST API is a python based microservice which is responsible for all the attendance related transactions in the OT-Microservices. 

## Purpose 
The Attendance REST API is a Python-based microservice designed to handle all attendance-related operations within the OT-Microservices ecosystem. Its primary goal is to provide a reliable, cross-platform, and scalable service that can record, retrieve, and manage attendance data efficiently.

## System Requirements
| System Requirement | Minimum Requirement |
|--------------------|----------------------|
| **OS**              | Ubuntu  |
| **Disk space**      | 20 GB |
| **RAM**             | 4 GB |
| **Processor**       | Dual-core recommended |
| **Instance Type**   | t2.small 

## Pre-requisites
## Build Time Dependencies

| Name            | Description     |
|--------------|-----------------|
| Poetry  |   |
|Make | |
|Liquibase | |
|Gunicorn|  |

## Run Time Dependencies

| Name           | Description     |
|---------------|-----------------|
| PostgreSql   |  |
| Redis  |   |
| Swagger|  | 
 


## Important Ports

| Inbound Traffic | Description       |
|------------------|-------------------|
|    6379      | redis |
|    5732     |  postgres |
|    8080      |   gunicorn |
|   22    |  SSh|
  |80         | network external|

## Architecture 

![image](https://github.com/user-attachments/assets/00ef17c0-ae63-4a65-8646-d98989d65b44)

## POC For Setup Attandance Api 
[Click here for Setup and run the App for POC](https://github.com/Cloud-NInja-snaatak/Documentation/blob/Shrey-SCRUM-70/ot_ms_understanding/application/attendance/setup.md)

## Components 

### PostgreSQL
### Redis
### Poetry 
### Liquibase
### Gunicorn 
## Contacts 
## References  

