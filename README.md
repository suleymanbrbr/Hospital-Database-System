# Hospital Database Management System

## Project Overview

This project is a Hospital Database Management System designed to manage patient information, appointments, surgeries, billing, and staff assignments. The system is implemented using a relational database schema, which ensures data integrity and supports various queries and operations.

## Entity-Relationship Diagram

The ER diagram provided outlines the relationships between different entities in the system, including patients, medical records, appointments, surgeries, billing, rooms, and staff (nurses and doctors). Each entity has its own attributes and is connected to others through various relationships to represent the hospital's operations comprehensively.

![ER Diagram](path_to_ER_model.png)

## Database Schema

### Tables

1. **Patients**
    ```sql
    CREATE TABLE Patients(
        p_id INT,
        gender VARCHAR(1),
        p_name VARCHAR(50),
        contact VARCHAR(50),
        bday DATE,
        PRIMARY KEY (p_id)
    );
    ```

2. **Stays_in_room**
    ```sql
    CREATE TABLE stays_in_room(
        p_id INT,
        room_id INT,
        stay_in DATE,
        PRIMARY KEY (p_id, room_id),
        FOREIGN KEY (p_id) REFERENCES Patients (p_id) ON DELETE CASCADE,
        FOREIGN KEY (room_id) REFERENCES Rooms (room_id) ON DELETE CASCADE
    );
    ```

### Functional Dependencies and BCNF

- **Patients Table**: The table is in Boyce-Codd Normal Form (BCNF). The only functional dependency is based on the primary key (p_id), which determines all other attributes. There are no partial dependencies.
  
- **Stays_in_room Table**: The table is in BCNF. The composite key (p_id, room_id) determines all other attributes.

### Sample Data Insertion

- **Patients Table**:
    ```sql
    INSERT INTO Patients (p_id, gender, p_name, contact, bday) VALUES
    (1, 'M', 'John Smith', 'john@gmail.com', '1990-05-15'),
    (2, 'F', 'Emily Johnson', 'emily@gmail.com', '1988-09-22'),
    (3, 'M', 'Michael Brown', 'michael@hotmail.com', '1992-03-10'),
    (4, 'F', 'Jessica Williams', 'jessica@gmail.com', '1995-11-27'),
    (5, 'M', 'William Taylor', 'william@hotmail.com', '1985-07-18'),
    (6, 'F', 'Sophia Anderson', 'sophia@gmail.com', '1998-01-03'),
    (7, 'M', 'Matthew Martinez', 'matthew@gmail.com', '1993-06-30'),
    (8, 'F', 'Emma Garcia', 'emma@gmail.com', '1991-12-14'),
    (9, 'M', 'Daniel Rodriguez', 'daniel@hotmail.com', '1987-04-28'),
    (10, 'F', 'Olivia Hernandez', 'olivia@hotmail.com', '1994-08-09');
    ```

- **Stays_in_room Table**:
    ```sql
    INSERT INTO stays_in_room (p_id, room_id, stay_in) VALUES
    (1, 101, '2024-04-23'),
    (2, 102, '2024-04-22'),
    (3, 103, '2024-04-21'),
    (4, 104, '2024-04-20'),
    (5, 102, '2024-04-19'),
    (6, 106, '2024-04-18'),
    (7, 107, '2024-04-17'),
    (8, 104, '2024-04-16'),
    (9, 109, '2024-04-15'),
    (10, 110, '2024-04-14');
    ```

### Queries

1. **Retrieve the names and contacts of patients who have a medical record in room 102**:
    ```sql
    SELECT Patients.p_name, Patients.contact 
    FROM Patients
    JOIN stays_in_room ON Patients.p_id = stays_in_room.p_id
    WHERE stays_in_room.room_id = 102;
    ```

2. **Calculate the total number of stays and the average age of patients for each room between April 15, 2024, and April 22, 2024**:
    ```sql
    SELECT room_id, COUNT(*) AS total_stays, AVG(DATEDIFF(CURDATE(), Patients.bday)/365) AS avg_age
    FROM stays_in_room
    JOIN Patients ON stays_in_room.p_id = Patients.p_id
    WHERE stay_in BETWEEN '2024-04-15' AND '2024-04-22'
    GROUP BY room_id;
    ```

### Constraints

- **Gender Check Constraint**:
    ```sql
    ALTER TABLE Patients
    ADD CONSTRAINT chk_gender CHECK (gender = 'M' OR gender = 'F');
    ```

### Error Handling

An attempt to insert an invalid gender value will result in an error:
```sql
INSERT INTO Patients (p_id, gender, p_name, contact, bday) VALUES (11, 'X', 'Alex', 'alex@example.com', '1990-01-01');
-- Error Code: 3819. Check constraint 'chk_gender' is violated.
```

## Project Phases

The project is divided into multiple phases, each building upon the previous one to enhance the database design and functionality. Detailed documentation for each phase can be found in the respective files.

- **[Phase 2 Documentation](path_to_phase_2.pdf)**
- **[Phase 3 Documentation](path_to_phase_3.zip)**
- **[Phase 4 Documentation](path_to_phase_4.zip)**

## Installation

To set up the database, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/your_username/hospital-database.git
    ```

2. Navigate to the project directory:
    ```bash
    cd hospital-database
    ```

3. Import the SQL scripts into your database management system.

## Usage

Use the provided SQL scripts to create tables, insert data, and run queries. Modify the scripts as needed to fit your specific requirements.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request with your changes.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to customize this README file further based on your project specifics and any additional information you want to include.
