
# Hospital Database Management Project

## Overview

This project is a comprehensive hospital database system designed to manage patient records, medical appointments, billing, and staff information. It is structured in multiple phases, each building on the previous to create a robust, normalized database that ensures data integrity and facilitates efficient data retrieval.

## ER Diagram

The Entity-Relationship (ER) diagram provides a visual representation of the hospital database schema, showing the relationships between different entities such as patients, doctors, nurses, appointments, surgeries, medical records, bills, and rooms. 

## Project Phases

### Phase 1: Initial Schema Design
- **Objective**: Create the initial ER diagram and define the basic schema of the database.
- **Entities**: Patients, Doctors, Nurses, Appointments, Surgeries, Medical Records, Bills, Rooms, Departments.
- **Relationships**: Defined relationships such as patients having medical records, making appointments, undergoing surgeries, and receiving bills.

### Phase 2: Database Normalization and Basic Operations
- **Objective**: Normalize the database schema to ensure it adheres to the Boyce-Codd Normal Form (BCNF).
- **Tasks**:
  - Create tables with appropriate constraints and keys.
  - Insert sample data into tables.
  - Perform basic queries to retrieve and manipulate data.
- **Tables Created**:
  - `Patients` with fields: `p_id`, `gender`, `p_name`, `contact`, `bday`.
  - `Stays_in_room` with fields: `p_id`, `room_id`, `stay_in`.

### Phase 3: Advanced Querying and Data Manipulation
- **Objective**: Enhance the database with more complex querying capabilities and additional constraints.
- **Tasks**:
  - Add constraints such as check constraints to ensure data validity.
  - Write and test advanced SQL queries for more sophisticated data retrieval.
- **Sample Queries**:
  - Retrieve names and contacts of patients with medical records in a specific room.
  - Calculate the total number of stays and average age of patients for each room within a date range.


### Phase 4 Overview

This project is designed to create a review management system using MongoDB Atlas. The system allows users to perform CRUD (Create, Read, Update, Delete) operations on two collections: `DoctorReviews` and `HospitalReviews`. The collections are designed to store reviews related to doctors and hospitals, respectively. The functionality is implemented using Python and the PyMongo library.

### System Functionality

The application provides the following functionalities:
1. Create a collection.
2. Read all data in a collection.
3. Read data with filters.
4. Insert data.
5. Delete data.
6. Update data.

### Collections

1. **DoctorReviews**: Stores reviews related to doctors, including the doctor's name, appointment time, and the review message.
2. **HospitalReviews**: Stores reviews related to hospitals, including the review date, review message, and rating.

### Code Implementation

#### Database Connection
The application establishes a connection to the MongoDB Atlas database using the PyMongo library.

#### CRUD Operations

1. **Creating a Collection**: 
   The application includes functionality to create new collections within the database.
   
2. **Insert Data**: 
   Users can insert new review data into the `DoctorReviews` and `HospitalReviews` collections.
   
3. **Read All Data in a Collection**: 
   The application can retrieve and display all data stored in a specific collection.
   
4. **Update Data**: 
   Existing review data in the collections can be updated based on specified criteria.
   
5. **Filtering Data**: 
   The application supports reading data with specified filters to retrieve relevant information.
   
6. **Delete Data**: 
   Users can delete specific review data from the collections.


## How to Use

1. **Setup the Database**: Use the SQL scripts provided in each phase to create and populate the database tables.
2. **Run Queries**: Utilize the provided SQL queries to perform various data retrieval and manipulation tasks.
3. **Modify and Extend**: Customize the schema and queries as per your specific requirements.

## Repository Structure

- `ER MODEL.png`: Visual representation of the ER diagram.
- `Hospital Database Phase 2.pdf`: Detailed documentation of Phase 2, including SQL scripts and explanations.
- `Hospital Database Phase 3.zip`: Files and scripts for Phase 3.
- `Hospital Database Phase 4.zip`: Files and scripts for Phase 4.

## Contributors

- Süleyman Berber
- Emre Tuygan
- Hüseyin Doğan Türk

