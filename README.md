# Task2 – Source Excel → Merge → Load into SQL Server (SSIS)

This SSIS project automatically loads data from **multiple Excel files** using a **Foreach Loop Container**, merges (appends) the records from each file, and stores the consolidated data into a **SQL Server table (SSMS / AWS RDS – SQL Server)**.

The complete process is executed in a **single run** and supports dynamic file iteration.

---

## 📌 Project Objective

The objective of this task is to:

- Read data from **three Excel source files**
- Iterate through all files dynamically
- Merge all records
- Load the final data into a single SQL Server destination table

---

## 🛠 Tools & Technologies

- SQL Server Integration Services (SSIS)
- Microsoft Excel (Source files)
- SQL Server (Local – SSMS)
- AWS RDS – SQL Server (Cloud database)
- Visual Studio (SSDT)

---

## 📂 Source Excel Files

All Excel files follow the same structure and contain a worksheet named:


### Excel 1

<img width="497" height="247" alt="Excel1" src="https://github.com/user-attachments/assets/a0f24a4b-c11e-4f60-a2c4-7bf03083e965" />

---

### Excel 2

<img width="494" height="256" alt="Excel2" src="https://github.com/user-attachments/assets/d23bb25a-b11b-4021-af84-15b6b8841aaf" />

---

### Excel 3

<img width="542" height="249" alt="Excel3" src="https://github.com/user-attachments/assets/4e26345e-8b91-4e23-86f1-de9995fdd45c" />

---

## 🧩 Solution Structure

The overall SSIS solution flow is shown below.

<img width="331" height="309" alt="Structure" src="https://github.com/user-attachments/assets/eec9bc1c-f1de-4580-b0b2-ea62030a36a2" />

---

## 🧭 Control Flow Design

The Control Flow contains:

- Execute SQL Task
- Foreach Loop Container
- Data Flow Task (inside the Foreach Loop)

<img width="751" height="718" alt="ES tASK" src="https://github.com/user-attachments/assets/7a21a2c9-5c66-4e00-b906-61a739b1232a" />

---

## 🗑 Execute SQL Task – Table Cleanup

Before loading new data, the destination table is cleared using the following query:

```sql
TRUNCATE TABLE Task2;
## 🔁 Foreach Loop Container – File Iteration

The Foreach Loop Container is configured to iterate through all Excel files present in a specified folder.

<img width="748" height="716" alt="Foreach Configration" src="https://github.com/user-attachments/assets/380c7dfe-25ab-48e8-ad97-c68e51d71bff" />

### ⚙ Enumerator Configuration

- **Enumerator Type**

