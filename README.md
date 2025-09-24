# PySpark Task

## 📌 Overview
This project contains a set of **PySpark exercises** implemented in `Task.ipynb`.  
It covers:
- RDD operations  
- DataFrame operations (filtering, grouping, aggregations)  
- Handling missing values  
- Word count and text processing  

The project can be run **locally** or using a **Docker Compose cluster** (with Spark, HDFS, and Jupyter).  

---

## 🛠️ Requirements
- Python 3.7+ (if running locally)  
- Docker & Docker Compose (for containerized setup)  
- VS Code with Jupyter extension  

---

## ▶️ Running with Docker

### 1️⃣ Start the Cluster
```bash
docker compose -f depi.yaml up -d
```

This will start the following containers:  
- **spark** (Spark master)  
- **spark-worker** (Spark worker)  
- **namenode** (HDFS namenode)  
- **datanode** (HDFS datanode)  
- **jupyter** (Jupyter Notebook server)

Check containers with:
```bash
docker ps
```

---

### 2️⃣ Access Jupyter
The Jupyter server runs on **`localhost:8888`**.  
Open it in your browser or directly in **VS Code**:  

- In VS Code, open the **Command Palette** → `Python: Specify Jupyter Server for Connections` → paste:  
  ```
  http://localhost:8888/?token
  ```
- You can get the token from logs:
  ```bash
  docker logs jupyter
  ```

---

### 3️⃣ Stop the Cluster
When finished:
```bash
docker compose -f depi.yaml down
```

---

## 📂 Dataset
- `NullData.csv` → sample sales data with missing values.  
- `russia.txt` → text file used for word count and text processing.  

These files should be placed inside the `/data/` directory (mapped to the Jupyter container).  

---

## 📘 Tasks Implemented

### 🔹 RDD Operations
- Create an RDD from a list of numbers.  
- Count even vs odd numbers.  
- Find the oldest person in a dataset.  
- Compute average age.  
- Group people by age.  

### 🔹 DataFrame Operations
- Show schema and rows.  
- Compute average salary.  
- Filter employees older than a given age.  
- Count distinct names.  
- Group by name and calculate average salary.  

### 🔹 Text Processing
- Count lines containing `"Russia"`.  
- Tokenize words.  
- Remove stopwords.  
- Count word frequencies and find top 5 frequent words.  

### 🔹 Null Handling
- Find average sales.  
- Replace null names with `"Unknown"`.  
- Replace null sales with the column average.  

---

## 📊 Example Output

**Average Salary**
```
6000.0
```

**Filter Employees Older than 28**
```
+---+------+---+------+
| id|  name|age|salary|
+---+------+---+------+
|  2|Mariam| 30|  6000|
|  3|  Omar| 35|  7000|
+---+------+---+------+
```
