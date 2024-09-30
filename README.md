# **Music Data Modeling and Query Performance Optimization Using MongoDB**

## **Project Overview**
This project focuses on designing two different MongoDB databases—**normalized** and **embedded**—to manage a dataset of songwriters and their recordings. By implementing various queries on both database models, the project explores how database structure impacts query performance. The project compares performance across a normalized model, where data is split into separate collections, and an embedded model, where related data is stored together in single documents.

---

## **Motivation**
Efficient data retrieval is critical when managing large datasets, particularly in industries such as music streaming and media management. The goal of this project is to evaluate how different database modeling strategies—**normalized** and **embedded**—affect query performance, especially for common operations like calculating song statistics or retrieving song information. The insights from this project will help in designing efficient MongoDB schemas for handling large and complex datasets.

---

## **Data and Setup**

### **Dataset**:  
The project uses two JSON datasets that represent songwriters and their recordings:
- **Songwriters**: Contains details about songwriters, such as their ID, name, reputation, and the IDs of their recordings.
- **Recordings**: Contains details about recordings, including the title, length, rhythmicality, issue date, and the IDs of the songwriters associated with each recording.

---

### **Database Models**:

1. **Normalized Model** (`db_Norm`): Two collections are created—`songwriters` and `recordings`—with relationships between them represented by foreign keys (IDs).
2. **Embedded Model** (`db_Embed`): All recordings for a songwriter are embedded directly in the `songwriters` collection, making it easier to retrieve all recordings of a songwriter without needing joins.

---

## **Project Structure**

### **Task Breakdown**

#### **Task 1: Create Normalized Database (`T1.py`)**
- This task involves creating a MongoDB database named `A4dbNorm`, which contains two collections: `songwriters` and `recordings`. These collections store normalized documents, and relationships between songwriters and recordings are maintained using IDs (foreign key relationships).

#### **Task 2: Create Embedded Database (`T2.py`)**
- This task creates another MongoDB database called `A4dbEmbed`. In this model, recordings are embedded directly within the songwriter documents, eliminating the need for joins when retrieving related data.

#### **Task 3: Query Performance Evaluation**
Each of the following queries is executed on both the normalized and embedded models, and performance is compared:

- **Query 1**: Find songwriters with at least one recording and count the number of recordings for each songwriter.
- **Query 2**: Calculate the average rhythmicality of recordings where the `recording_id` starts with "70".
- **Query 3**: Find the total length of all recordings for each songwriter.
- **Query 4**: For recordings issued after January 1, 1950, retrieve the songwriter name, recording name, and issue date.

For each query, two Python applications are created:
- **Qx_Norm.py**: Runs the query on the `A4dbNorm` database (normalized model).
- **Qx_Embed.py**: Runs the query on the `A4dbEmbed` database (embedded model).

### **Files and Scripts**:

- `T1.py`: Creates the normalized MongoDB database (`A4dbNorm`).
- `T2.py`: Creates the embedded MongoDB database (`A4dbEmbed`).
- `Q1_Norm.py`, `Q1_Embed.py`: Executes Query 1 on the normalized and embedded models, respectively.
- `Q2_Norm.py`, `Q2_Embed.py`: Executes Query 2 on the normalized and embedded models, respectively.
- `Q3_Norm.py`, `Q3_Embed.py`: Executes Query 3 on the normalized and embedded models, respectively.
- `Q4_Norm.py`, `Q4_Embed.py`: Executes Query 4 on the normalized and embedded models, respectively.

---

## **Results**
The performance of each query is compared across the normalized and embedded models. The key findings include:
- **Normalized Model**: More flexible for complex queries but slower due to the need for joins between collections.
- **Embedded Model**: Faster for queries that retrieve all related data for a single songwriter, but it introduces redundancy and potential scalability issues as data size grows.

The results for each query are visualized to highlight the performance trade-offs between these two data models.

---

## **Technologies Used**
- **MongoDB**: For database management and query execution.
- **PyMongo**: A Python library for interacting with MongoDB, used for querying and data manipulation.
- **Python**: For scripting and automating the creation and querying of databases.
- **Matplotlib**: Used for visualizing query performance.

---

## **Conclusion**
This project demonstrates the impact of data modeling strategies on MongoDB query performance. By comparing the normalized and embedded models, the project provides valuable insights into which model is more suitable for specific types of queries. For read-heavy applications with complex relationships, the normalized model may be better, while the embedded model is advantageous for quick, single-document reads. The choice of model depends on the expected usage patterns of the database.

---

## **How to Run the Project**

1. **Set up MongoDB**: Ensure MongoDB is installed and running on your local machine.
2. **Create the databases**:
   - Run `T1.py` to create the normalized database:
     ```bash
     python3 T1.py <port>
     ```
   - Run `A4T2.py` to create the embedded database:
     ```bash
     python3 T2.py <port>
     ```

3. **Execute Queries**:
   - Run the query scripts on both databases:
     ```bash
     python3 Q1_Norm.py <port>
     python3 Q1_Embed.py <port>
     # Repeat for all other query scripts (Q2, Q3, Q4)
     ```

4. **Analyze the results**: Compare the performance results between the normalized and embedded models.

---

## **Acknowledgements**
This project is inspired by database modeling concepts and performance optimization using MongoDB. The datasets used are simulated music data representing songwriters and their recordings.

---