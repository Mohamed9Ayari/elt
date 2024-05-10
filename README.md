# My Custom ELT Project

Welcome to my personal Extract, Load, Transform (ELT) project! This project showcases a customized ELT process using Docker and PostgreSQL.

## Repository Structure

- **docker-compose.yaml**: Configuration file for Docker Compose, managing multiple Docker containers.
  - `source_postgres`: Source PostgreSQL database.
  - `destination_postgres`: Destination PostgreSQL database.
  - `elt_script`: Service executing the ELT script.
- **elt_script/Dockerfile**: Sets up Python environment, installs PostgreSQL client, and includes the ELT script.
- **elt_script/elt_script.py**: Python script for the ELT process.
- **source_db_init/init.sql**: SQL script initializing the source database with sample data.

## How this Project Works

### Docker Compose
I use Docker Compose to orchestrate three containers:
1. Source PostgreSQL database with sample data.
2. Destination PostgreSQL database.
3. Python environment executing the ELT script.

### ELT Process
1. The file `elt_script.py` waits for the source PostgreSQL database to become available.
2. Upon availability, it uses `pg_dump` to export data to a SQL file.
3. Then, it imports this SQL file into the destination PostgreSQL database using `psql`.

### Database Initialization
The `init.sql` script sets up the source database with sample data, creating and populating tables.

## Getting Started

1. Make sure you have Docker and Docker Compose installed.
2. Clone this repository to your local machine.
3. Navigate to the project directory and run `docker-compose up`.
4. Once all containers are up, the ELT process begins automatically.
5. Upon completion, you can access the source and destination PostgreSQL databases via ports 5433 and 5434, respectively.

Feel free to explore and modify this project according to your needs. Happy ELT-ing!
