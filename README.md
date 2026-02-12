# Task 2 — Source Excel Merge and Load into SSMS

This SSIS project automates the process of loading data from multiple Excel files into SQL Server. Using a **Foreach Loop Container**, the solution iterates through all Excel files in a specified folder, appends their records, and consolidates the data into a single SQL Server table. The workflow ensures seamless integration and eliminates manual effort in merging files.

---

## 🛠 Tools & Technologies

- **SQL Server Integration Services (SSIS)**
- **Microsoft Excel** (Source files)
- **SQL Server** (Local database)
- **AWS RDS – SQL Server** (Cloud database)
- **Visual Studio (SSDT)**

---

## 📂 Project Workflow

### 1. Source Files
Three Excel files (`Excel1.xlsx`, `Excel2.xlsx`, `Excel3.xlsx`) serve as input data sources.  
Each file contains a sheet named **Data$** which is read during execution.

#### Excel 1
<img width="497" height="247" alt="Excel1" src="https://github.com/user-attachments/assets/a0f24a4b-c11e-4f60-a2c4-7bf03083e965" />

#### Excel 2
<img width="494" height="256" alt="Excel2" src="https://github.com/user-attachments/assets/d23bb25a-b11b-4021-af84-15b6b8841aaf" />

#### Excel 3
<img width="542" height="249" alt="Excel3" src="https://github.com/user-attachments/assets/4e26345e-8b91-4e23-86f1-de9995fdd45c" />

---

### 2. Control Flow

#### Structure of Solution Flow
<img width="331" height="309" alt="Structure " src="https://github.com/user-attachments/assets/eec9bc1c-f1de-4580-b0b2-ea62030a36a2" />

#### Execute SQL Task
<img width="751" height="718" alt="ES tASK " src="https://github.com/user-attachments/assets/7a21a2c9-5c66-4e00-b906-61a739b1232a" />

- Runs at the beginning of the package.  
- Executes:  
  ```sql
  TRUNCATE TABLE Task2;

### 3. Data Flow
- Data Flow Task
<img width="763" height="669" alt="DataFlow Task" src="https://github.com/user-attachments/assets/e327de3f-083e-4254-a760-b98af0bd686b" />

- Present inside the Foreach Loop Container.

- Contains:

- Excel Source (reads data from Excel files)

- OLE DB Destination (loads data into SQL Server)

-- Excel Source Configuration
<img width="775" height="727" alt="Excel Config " src="https://github.com/user-attachments/assets/0f8d09f9-7ca8-474b-ac4c-c814c20ebc0f" />
- Connection Manager created for Excel.

Reads from sheet Data$.

- Excel Connection Manager Properties
<img width="1013" height="520" alt="Excel Connection managaer Config " src="https://github.com/user-attachments/assets/d9b57048-c12e-4e6e-9a0d-3ea88aa56681" />

- Configured with Expressions to dynamically update file path.

Example path:
C:\Users\Aum S\Desktop\Inkey Internship\SSIS\05-02-2026\Excel1.xlsx

- OLEDB Destination Configration
<img width="765" height="732" alt="Sql Configraion" src="https://github.com/user-attachments/assets/3adbc284-4fd0-4717-b8d7-8cb6df4c8ff2" />

### 4. Foreach Loop Configuration
<img width="748" height="716" alt="Foreach Configration " src="https://github.com/user-attachments/assets/380c7dfe-25ab-48e8-ad97-c68e51d71bff" />

- Enumerator: For Each File Enumerator

- Folder Path: Location of Excel files

Files: *.xlsx

Retrieves fully qualified file names for processing.

✅ Execution Flow
Truncate Destination Table (Task2)

Iterate Excel Files using Foreach Loop

Load Data from each file via Excel Source

Append Records into SQL Server table

Final Output: Consolidated dataset stored in Task2

### 📊 Output
After execution, all records from the three Excel files are merged and stored in the SQL Server destination table.

<img width="461" height="625" alt="Screenshot (862)" src="https://github.com/user-attachments/assets/925d1673-d7b8-45e4-aca0-49a2bd46ae0b" />
