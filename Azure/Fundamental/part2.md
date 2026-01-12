Here are **detailed, structured notes** based on the transcript section you provided from the DP-900 certification video:

---

## 🧠 **Understanding the Value of DP-900 Certification**

### 📈 **Why Data Skills Matter Today**

- Over the past few decades, **web, mobile, and storage technologies** have evolved rapidly.
- This has led to a **massive increase in daily data generation**.
- Data is now **ubiquitous**—present in every domain and industry.
- It’s crucial to know:
  - How to **ingest** (collect and bring in) data
  - How to **process** data at scale
  - How to **extract meaningful insights** from data

---

### 🎯 **What is DP-900?**

- **DP-900** is a **Microsoft certification exam** focused on **fundamentals of data platforms**.
- It’s suitable for:
  - Beginners in data platforms
  - Professionals already using **Microsoft data technologies**
  - Anyone looking to **validate their knowledge** or **start a career in data**

---

### 💼 **Benefits of DP-900 Certification**

- Helps you:
  - **Prove your foundational knowledge** in data concepts
  - **Start your journey** in data-related roles
  - Possibly **earn a raise** or **move into a senior role**
- Acts as a **stepping stone** for more advanced certifications and roles in data engineering, analytics, and AI.

---

### 👨‍🏫 **Instructor Introduction**

- **Emilio Melo**:
  - Certified **Data Engineer Associate**
  - Former **Cloud Solutions Architect** for Data & AI at Microsoft
- His goal: Help you **pass the DP-900 exam on your first try**

---

### 📚 **Course Objective**

- Provide **comprehensive preparation** for the DP-900 exam
- Cover a **wide range of topics** related to data platforms
- Ensure you're ready to **understand, apply, and explain** core data concepts

---

## 🧾 **DP-900 Certification Overview**

### 🏷️ **Microsoft Certification Naming Convention**

- Microsoft uses a **consistent naming pattern** for its certifications:
  - **Fundamentals** level exams typically end in **900** (e.g., DP-900, AZ-900)
  - **Associate** level exams often end in **100 or 200** (e.g., DP-200, AI-102)
  - **Expert** level exams include **AZ-400, AZ-300, AZ-301**
  - There is also a **Specialty** level for niche areas like **IoT**, but it's less common

---

### 🧩 **Certification Levels Explained**

#### 1. **Fundamentals**

- Entry-level certifications
- Focus on **general concepts**, not deep technical details
- No coding or complex configuration questions
- Examples: **DP-900**, **AZ-900**

#### 2. **Associate**

- Designed for professionals with **~2 years of experience**
- More **technical and hands-on**
- Examples: **DP-200**, **AI-102**

#### 3. **Expert**

- Highest level of difficulty and prestige
- Requires **deep technical knowledge**
- Examples: **AZ-400**, **AZ-300**, **AZ-301**

---

### 🔤 **Prefix Meaning in Exam Codes**

- **DP** = Data Platform
- **AI** = Artificial Intelligence
- **AZ** = Azure

These prefixes help identify the **domain** of the certification.

---

## 🎓 **What to Expect in the DP-900 Exam**

### 📌 **Exam Focus Areas**

- **Relational databases** (e.g., SQL Server, Azure SQL)
- **Non-relational databases** (e.g., Cosmos DB)
- **Modern data warehouse** concepts
- **Reporting tools** like **Power BI**
- **Data ingestion & processing tools**:
  - **Azure Data Factory**
  - **Databricks**
  - **HDInsight**

### ❌ **What’s Not Included**

- No coding questions
- No UI-based questions (e.g., which button to click)

---

## 📚 **Course Design & Learning Approach**

- The course is **aligned with the DP-900 exam structure**
- Focuses on **conceptual understanding**, not implementation
- Includes **demos** to showcase technology capabilities
- Provides **LinkedIn Learning references** for deeper exploration

---

## 🧠 **Prerequisites & Recommendations**

- No strict prerequisites
- Helpful if you have:
  - Basic **Azure** experience
  - Some **database** knowledge
  - Familiarity with **development concepts**

---

## 🧠 **Core Data Concepts in Modern Business**

### 📊 **Why Data Matters**

- Data is often called **“the new oil”** because:
  - It fuels **business intelligence** and **competitive advantage**
  - Helps in **decision-making**, **strategy**, and **innovation**
- Traditionally, BI (Business Intelligence) required:
  - Expensive hardware
  - Costly software licenses
  - Specialized expertise
- Today, data is:
  - **Cheaper and easier** to collect, store, and analyze
  - **Accessible** even to **small and mid-sized businesses**

---

## 📘 **What is Data?**

- Data = **Collection of facts** (numbers, descriptions, observations)
- Used for **decision-making**
- Can be categorized into **three types**:
  1. **Structured Data**
  2. **Semi-Structured Data**
  3. **Unstructured Data**

---

### 1️⃣ **Structured Data**

- Organized in **rows and columns** (tabular format)
- Stored in **relational databases**
- Requires a **predefined schema** (data structure known in advance)
- Common relational database systems:
  - **SQL Server**
  - **Oracle**
  - **Db2**
  - **MySQL**
- Best for situations where **data format is predictable**

---

### 2️⃣ **Semi-Structured Data**

- Doesn’t follow a rigid schema like relational databases
- Still has **some structure**
- Common formats:
  - **XML** (Extensible Markup Language)
  - **JSON** (JavaScript Object Notation)
  - **Key-value pairs**
  - **Graph formats**
- Technologies that support semi-structured data:
  - **Azure Tables**
  - **Cosmos DB**
  - **MongoDB**
  - **Cassandra**
- Useful when **data format is flexible or evolving**

---

### 3️⃣ **Unstructured Data**

- No predefined structure or searchable fields
- Examples:
  - **Audio files**
  - **Video files**
  - **Images**
  - **Documents** (Word, Excel, PDFs)
- Requires **specific software** to open and interpret
- Harder to analyze at scale compared to structured/semi-structured data

#### 🔒 **Storage Options for Unstructured Data**

- **File servers**
- **SharePoint**
- **Azure services**:
  - **Azure Files**
  - **Azure Data Lake**
  - **Blob Storage** (Binary Large Object)

---

## ⚙️ **Data Processing Concepts**

### 🔄 **What is Data Processing?**

- **Definition**: Converting **raw data** into **meaningful information** after it has been **ingested and collected**
- Two main types:
  1. **Batch Processing**
  2. **Streaming Processing**

---

## 🗂️ **1. Batch Processing**

### 📌 **How It Works**

- Data is **collected into groups (batches)** and processed **later**, based on:
  - **Time intervals** (e.g., every hour, daily)
  - **Data volume** (e.g., every 10 GB)
  - **Events** (e.g., when server CPU < 10%)

### 🧾 **Real-Life Examples**

- Monthly credit card bills
- Salary payments
- Mobile recharge expirations

### ✅ **Advantages**

- Efficient for **large data volumes**
- Can be scheduled during **off-peak hours** (e.g., nights, weekends)

### ❌ **Disadvantages**

- **High latency**: Not suitable for **real-time** or **time-sensitive** tasks
- Example: Traffic control systems need real-time data, not overnight processing

---

## 🌊 **2. Streaming Processing**

### 📌 **How It Works**

- Data is processed **immediately as it arrives**
- Ideal for **real-time**, **time-critical** operations

### 🧾 **Use Cases**

- **IoT devices** sending telemetry data
- **Online gaming** tracking player actions in real time
- **Stock market** monitoring and trading

---

## 🔍 **Batch vs. Streaming: Key Differences**

| Aspect          | Batch Processing                          | Streaming Processing               |
| --------------- | ----------------------------------------- | ---------------------------------- |
| **Data Scope**  | Entire dataset                            | Recent data (e.g., last hour)      |
| **Data Size**   | Large volumes                             | Small, real-time chunks            |
| **Performance** | High latency (hours/days)                 | Low latency (seconds/milliseconds) |
| **Analysis**    | Complex analytics (e.g., BI, warehousing) | Simple, reactive analytics         |

---

## 🔁 **ETL vs. ELT in Data Processing**

### 🧱 **ETL (Extract, Transform, Load)**

- **Traditional approach**
- Steps:
  1. **Extract** data from source
  2. **Transform** it (filter, sort, clean)
  3. **Load** into destination (e.g., Data Warehouse)
- ✅ Ensures **clean, structured, compliant** data
- ❌ Requires **more upfront work**

### ⚡ **ELT (Extract, Load, Transform)**

- **Modern approach**
- Steps:
  1. **Extract** data
  2. **Load** into destination
  3. **Transform** using destination system
- ✅ More **agile**, supports **experimentation**
- Enabled by:
  - **Cheaper storage**
  - **Technologies** like:
    - **PolyBase**
    - **Data Lakes**
    - **MPP systems** (e.g., Azure Synapse Analytics)

---

## 🛠️ **Microsoft Tools for ETL/ELT**

| Environment     | Tool Name                                  |
| --------------- | ------------------------------------------ |
| **On-premises** | SQL Server Integration Services (**SSIS**) |
| **Cloud**       | **Azure Data Factory**                     |

---

## 📊 **Data Analytics Categories**

### 🧠 **What is Data Analytics?**

- **Definition (Wikipedia)**:  
  The process of **inspecting**, **cleansing**, **transforming**, and **modeling** data to:
  - Discover useful information
  - Inform conclusions
  - Support decision-making

### 💡 **Real-World Examples**

- Product recommendations (e.g., shopping sites)
- Movie suggestions (e.g., streaming platforms)
- Targeted ads on social media

These are all **applications of data analytics** that help businesses gain a **competitive edge**.

---

## 🧭 **Five Categories of Data Analytics**

### 1️⃣ **Descriptive Analytics**

- **Purpose**: Understand **what happened** in the past
- **Examples**:
  - Total sales last year
  - Percentage of customers lost to competitors
- **Output**: Reports that **summarize historical data**

---

### 2️⃣ **Diagnostic Analytics**

- **Purpose**: Understand **why something happened**
- **Examples**:
  - Customer churn linked to competitor’s product launch
- **Output**: Insights into **causes and correlations**

---

### 3️⃣ **Predictive Analytics**

- **Purpose**: Forecast **what will happen**
- **Techniques**: Uses **machine learning** (e.g., classification, regression)
- **Examples**:
  - Predicting stock prices
  - Assessing loan default risk
- **Output**: **Probabilistic forecasts** based on patterns

---

### 4️⃣ **Prescriptive Analytics**

- **Purpose**: Recommend **what to do next**
- **Builds on**: Predictive analytics
- **Examples**:
  - Suggest slowing down a machine to prevent failure
  - Optimize maintenance schedules
- **Output**: **Actionable recommendations**

---

### 5️⃣ **Cognitive Analytics**

- **Purpose**: Mimic human thought to **infer patterns and meaning**
- **Techniques**: Uses **Artificial Intelligence (AI)** and **Natural Language Processing (NLP)**
- **Examples**:
  - Transcribing audio to text
  - Detecting objects in images
  - Translating languages
  - Identifying anomalies
- **Microsoft Tool**: **Cognitive Services APIs**

---

## 📚 **Additional Learning Resources for Core Data Concepts**

### 🧾 **Exam Scope Reminder**

- The **DP-900 exam** focuses on **concepts**, not deep **implementation** or **coding**
- This course is designed to match that scope

---

### 🌐 **Recommended Resource: Microsoft Learn**

- **Microsoft Learn** is the **best platform** for exploring topics covered in the DP-900 exam
- Offers:
  - **Free, interactive tutorials**
  - **Hands-on labs**
  - **Conceptual explanations**
  - **Practice modules**
- The content on Microsoft Learn **closely aligns** with the DP-900 exam objectives

---

### 🔗 **Topics Covered So Far**

- Data types: Structured, Semi-Structured, Unstructured
- Data processing: Batch vs. Streaming
- ETL vs. ELT
- Data analytics categories: Descriptive, Diagnostic, Predictive, Prescriptive, Cognitive

For deeper understanding of these topics, Microsoft Learn provides **step-by-step guides** and **real-world examples**.

---

## 🗃️ **Relational Data Concepts**

### 🧾 **What Are Relational Databases?**

- A **widely used method** for storing and retrieving data
- Common across businesses of **all sizes** for **decades**
- Known for a **simple, well-understood model**:  
  → **Data stored in tables**

### ✅ **Use Cases**

- Ideal when **strong consistency** is required
- Examples:
  - **Banking systems**
  - **E-commerce platforms**
  - **Flight and hotel reservation systems**

---

## 📐 **Core Elements of Relational Databases**

### 📊 **Tables**

- Basic unit of data storage
- Organized in **rows and columns**
- Each row has a **fixed set of columns**
- Can be **empty** or contain **multiple rows**

---

### 🔑 **Primary Key**

- A column (or combination of columns) that **uniquely identifies** each row
- **No two rows** can have the same primary key

---

### 🔗 **Foreign Key**

- A column that **references a primary key** in another table
- Used to **link tables together**
- Example:
  - In an **Orders** table, `CustomerID` is a foreign key pointing to the **Customers** table

---

### 🔁 **Cardinality**

- Defines the **type of relationship** between tables:
  - **One-to-One**
  - **One-to-Many** (e.g., one customer → many orders)
  - **Many-to-Many**

---

### 👁️ **Views**

- A **virtual table** created from a query
- Helps:
  - Filter columns (vertical filtering)
  - Restrict rows (horizontal filtering)
- Makes data **more relevant** for specific users

---

### 🔍 **Indexes**

- Improve **search performance**, especially on **large tables**
- Require **extra space** and **maintenance**
- Two types:
  1. **Clustered Index**
     - Physically organizes data in the table
     - Only **one per table**
     - Should be created on the **most searched column**
  2. **Non-Clustered Index**
     - Logical pointers to data
     - Can have **multiple per table**
     - Useful for **frequently searched columns**

---

### 🧮 **Programmability Objects**

- Used to **automate and reuse** logic
- Includes:
  - **Stored Procedures**
  - **Functions**
- Can accept **input/output parameters**
- Useful for **repeatable operations**

---

### 📌 **Exam Focus**

- DP-900 focuses on **high-level concepts**
- No need to worry about:
  - Implementation details
  - Architecture
  - Deep coding

---

## ☁️ **Hosting Models: On-Premises vs. Cloud Services**

Understanding the differences between hosting models is essential for choosing the right infrastructure for your data platform.

---

### 🏢 **1. On-Premises Hosting**

#### 📌 Overview

- Traditional model used **before cloud adoption**
- Still required in **highly regulated industries** where cloud is restricted

#### 🧰 Responsibilities

- You manage **everything**:
  - Hardware
  - Software
  - Cabling
  - Backups
  - Virtual Machines (VMs)
  - Storage

#### 💸 Characteristics

- **High upfront costs**
- **Limited scalability**
- Example technologies:
  - **SQL Server**
  - **Windows Server 2019** (file server)

---

### 🖥️ **2. IaaS – Infrastructure as a Service**

#### 📌 Overview

- Hosting **VMs on public cloud** (e.g., Azure)
- Works on a **subscription model** (no upfront costs)

#### 🧰 Responsibilities

- Cloud provider handles **hardware**
- You manage:
  - Operating system
  - Backups
  - Patching
  - Software installation & licensing

#### 🧳 Use Case

- Ideal for **“lift and shift”** migrations
- Example: **SQL Server on Azure VM**

---

### 🧱 **3. PaaS – Platform as a Service**

#### 📌 Overview

- Higher abstraction than IaaS
- Cloud provider manages:
  - Hardware
  - Backups
  - Patching
  - High availability

#### 💡 Benefits

- **Easy scaling**
- **Licensing included** in service cost
- Option to use **Azure Hybrid Benefit (AHUB)** if you have existing licenses

#### 🧳 Examples

- **Cosmos DB**
- **Azure Storage**
- PaaS versions of:
  - **SQL Server**
  - **PostgreSQL**
  - **MySQL**
  - **MariaDB**

---

### 📦 **4. SaaS – Software as a Service**

#### 📌 Overview

- **Highest level of abstraction**
- Minimal configuration required
- **Maintenance handled** by cloud provider

#### 🧳 Examples

- **Office 365**
- **Dynamics 365**
- **Power BI**

---

## 🗃️ **Relational Database Offerings in Azure**

Azure provides multiple options for hosting relational databases, depending on your needs for control, scalability, and maintenance.

---

### 🖥️ **1. SQL Server on Azure Virtual Machine (IaaS)**

#### 📌 Overview

- Equivalent to running **SQL Server on-premises**, but hosted in the cloud
- No learning curve if you're familiar with traditional SQL Server

#### 🧰 Responsibilities

- You manage:
  - **Patching**
  - **Backups**
  - **Licensing**
  - **OS-level tasks**

#### 🧳 Use Case

- Ideal for **lift-and-shift** migrations
- Useful when your application depends on **SQL Server features** not supported in PaaS offerings

---

### ☁️ **2. Azure SQL Database (PaaS)**

#### 📌 Overview

- Fully managed **Platform as a Service (PaaS)** offering
- Abstracts away many administrative tasks

#### 🧰 Features Managed by Azure

- **Backups**
- **Patching**
- **Encryption**
- **High availability**
- **Advanced threat protection**

#### 📈 Benefits

- **99.9% uptime SLA**
- **Easy scalability**
- **No upfront costs**
- **SQL license included** in service pricing

#### 🧳 Business Critical Tier

- Offers:
  - **Lower latency**
  - **Higher availability**
  - **Read-only replicas** for reporting (without affecting production)

---

## 🔍 **Querying Relational Data in Azure**

### 🧾 **SQL Language Overview**

- **SQL (Structured Query Language)**:
  - Created in the **1970s**
  - Standardized by **ANSI and ISO** in **1987**
  - Main language for querying **relational databases**

### 🧩 **SQL Dialects by Platform**

| Platform   | SQL Dialect          |
| ---------- | -------------------- |
| SQL Server | Transact-SQL (T-SQL) |
| Oracle     | PL/SQL               |
| PostgreSQL | pgSQL                |

- Use **platform-specific dialects** for advanced features
- Use **ANSI SQL** for **cross-platform compatibility**

---

## 🧱 **SQL Command Categories**

### 1️⃣ **DML – Data Manipulation Language**

- Used for **CRUD operations** (Create, Read, Update, Delete)
- Common commands:
  - `SELECT`: Read/query data
  - `INSERT`: Add new records
  - `UPDATE`: Modify existing records
  - `DELETE`: Remove records
  - `MERGE`: Combine insert/update/delete (less likely on exam)

#### 🧾 **SELECT Syntax Overview**

```sql
SELECT column1, column2
FROM table_name
WHERE condition;
```

- `WHERE` clause filters data (important for `UPDATE` and `DELETE`)
- Use `JOIN` to combine data from multiple tables:
  - Types: `INNER JOIN`, `CROSS JOIN`, `FULL JOIN`, etc.
- Use **functions** like `MAX()` for calculations

---

### 2️⃣ **DDL – Data Definition Language**

- Used to **create and manage database objects**
- Common commands:
  - `CREATE`: Create new object (e.g., table)
  - `ALTER`: Modify object
  - `RENAME`: Rename object
  - `DROP`: Delete object (⚠️ irreversible)

#### 🧾 **Example: Creating a Table**

```sql
CREATE TABLE Location (
  LocationID INT NOT NULL,
  Name NVARCHAR(50),
  CostRate DECIMAL(5,2),
  Availability FLOAT,
  ModifiedDate DATETIME
);
```

---

### 3️⃣ **DCL – Data Control Language**

- Used to **manage permissions**
- Commands:
  - `GRANT`
  - `REVOKE`
  - `DENY`

---

### 4️⃣ **TCL – Transaction Control Language**

- Used to **manage transactions**
- Commands:
  - `BEGIN TRAN`
  - `COMMIT TRAN`
  - `ROLLBACK TRAN`

---

## 🛠️ **Tools for Querying Azure Databases**

### 🖥️ **Graphical Tools**

| Tool                                    | Description                                                           |
| --------------------------------------- | --------------------------------------------------------------------- |
| **SQL Server Management Studio (SSMS)** | Free, widely used for SQL Server and Azure SQL                        |
| **Visual Studio (Community Edition)**   | With SQL Server Data Tools (SSDT) for offline development             |
| **Azure Portal Query Tool**             | Built-in query interface for Azure SQL                                |
| **MySQL Workbench**                     | For MySQL and MariaDB                                                 |
| **pgAdmin**                             | For PostgreSQL                                                        |
| **Azure Data Studio**                   | Cross-platform, extensible, supports notebooks and multiple databases |

### 💻 **Command-Line Tools**

| Database      | CLI Tool |
| ------------- | -------- |
| Azure SQL     | `SQLCMD` |
| MySQL/MariaDB | `mysql`  |
| PostgreSQL    | `psql`   |

- **Azure Cloud Shell** includes all these tools by default

---

## 🛠️ **Relational Data Management Tasks in Azure**

Managing relational databases in Azure involves tasks like provisioning, configuring, securing, and automating resources.

---

### 🖥️ **Management Tools**

#### 1️⃣ **Azure Portal**

- **Graphical interface** for creating and managing resources
- Uses **wizards** with built-in validation
- Most **user-friendly** option

#### 2️⃣ **Azure CLI (Command Line Interface)**

- Cross-platform: **Windows, macOS, Linux**
- Ideal for **automation** and **scripting**

#### 3️⃣ **Azure PowerShell**

- PowerShell extensions for Azure
- Also cross-platform
- Choice between CLI and PowerShell depends on **personal preference**

#### 4️⃣ **ARM Templates (Azure Resource Manager)**

- **JSON files** that define resource configurations
- Used for **automated provisioning**
- Can be deployed via **CLI or PowerShell**

---

### ⚙️ **Provisioning**

- Refers to **setting up resources** in Azure
- Includes:
  - Allocating **CPU, memory, disk**
  - Configuring **scaling options**

---

## 🔐 **Security Components**

### 1️⃣ **Firewalls**

- All Azure databases (SQL, MySQL, MariaDB, PostgreSQL) have **server-level firewalls**
- **Default behavior**: All access is blocked
- You must:
  - **Configure firewall rules** to allow client connections
  - **Enable outbound traffic** on company firewalls
    - Ports:
      - PostgreSQL: `5432`
      - MySQL/MariaDB: `3306`

---

### 2️⃣ **Encryption**

- Ensures data is **not readable as plain text**
- Two types:
  - **In-transit**: SSL connections (enabled by default)
  - **At-rest**: Database-level encryption
    - Azure SQL uses **Transparent Data Encryption (TDE)**

---

### 3️⃣ **Advanced Threat Protection (ATP)**

- Detects **unusual activity** and **suspicious access**
- Available for:
  - Azure SQL
  - Azure Managed Instance (MI)
  - Synapse Analytics
  - Preview for MariaDB, MySQL, PostgreSQL

---

## 👤 **Authentication & Permissions**

### 🔑 **Authentication**

- Validates **user identity**
- Supported methods:
  - **SQL Authentication**
  - **Azure Active Directory (Azure AD)**
    - Not yet available for **Azure MariaDB**
- Azure AD is preferred:
  - **Centralized identity management**
  - Supports **Multi-Factor Authentication (MFA)**

---

### 🛂 **Permissions**

Two levels of access control:

#### 1. **Resource-Level Permissions**

- Control over:
  - CPU, memory
  - Firewall settings
  - Encryption
  - Auditing
- Managed via **Azure Role-Based Access Control (RBAC)**
  - Assign users to **built-in roles** for automatic permission setup

#### 2. **Database-Level Permissions**

- Control access to **tables, views, procedures**
- Common roles in **Azure SQL**:
  - `db_owner`: Full access
  - `db_ddladmin`: Can execute DDL commands
  - `db_datareader`: Can read all tables

---

## 🧪 **Working with Relational Databases in Azure**

This section provides a **hands-on overview** of creating and querying an Azure SQL Database using both the **Azure Portal** and **SQL Server Management Studio (SSMS)**.

---

### 🛠️ **Creating an Azure SQL Database (via Azure Portal)**

#### 📌 Steps:

1. **Go to Azure Portal** → Click **Create a Resource**
2. Search for **Azure SQL** → Click **Create**
3. Choose between:
   - **SQL Database**
   - **SQL Managed Instance (MI)**
   - **SQL Virtual Machine**
4. Select **SQL Database** → Click **Create**
5. Choose a **Resource Group**
6. Enter **Database Details**:
   - Name: `DP900_SQL_DB`
   - Create a new **SQL Server**:
     - Server name: `DP900_SQL`
     - Login: `DP900_admin`
     - Password: (set and confirm)
     - Region: e.g., **Southeast Asia**
7. Decide on **Elastic Pool** usage (not used in demo)
8. Configure **Database Tier**:
   - Choose **Basic** (low cost, light usage)
9. Set **Redundancy Level**: e.g., **LRS (Locally Redundant Storage)**
10. Configure **Networking**:
    - Enable **Public Endpoint** (for demo only)
    - Allow **Azure services** and **your IP** to connect
11. Select **Sample Database**:
    - **AdventureWorksLT** (lightweight demo database)
12. Click **Create** → Wait for deployment → Click **Go to Resource**

---

### 🔍 **Querying the Database**

#### 📌 Using Azure Portal Query Editor

- Navigate to **Query Editor**
- Authenticate with **username and password**
- Use **IntelliSense** to write SQL queries
- Example:
  ```sql
  SELECT * FROM Products;
  ```
- Run the query → View results

#### 📌 Using SQL Server Management Studio (SSMS)

- Open SSMS → Connect using:
  - Server name
  - Login
  - Password
- Open **New Query**
- Select the database: `DP900_SQL_DB`
- Paste and run the same query:
  ```sql
  SELECT * FROM Products;
  ```
- View results in SSMS

---

### 🧾 **Notes**

- **AdventureWorksLT** is a Microsoft demo database used for training
- **Basic tier** is suitable for learning and light workloads
- **Public endpoint** should be avoided in production for security reasons
- **SSMS** and **Azure Portal** both support querying and managing Azure SQL databases

---

## 📚 **Additional Resources for Learning Relational Databases**

If you want to go beyond the exam scope and explore **coding**, **implementation**, and **tool usage**, here are some recommended resources:

---

### 🧠 **Microsoft Learn**

- **Official learning platform** from Microsoft
- Offers **interactive tutorials**, **hands-on labs**, and **exam-focused content**
- Two key links mentioned:
  - One specifically designed for **DP-900 exam preparation**
  - Another covering **relational data fundamentals**

---

### 📘 **LinkedIn Learning Courses**

#### 1️⃣ **Learning Azure SQL Query – by Anton Delsink**

- Focuses on:
  - **SQL language basics**
  - Querying in the context of **Azure SQL**
- Great for understanding **real-world SQL usage**

#### 2️⃣ **Azure Data Studio Essential Training – by Adam Wilburt**

- Covers:
  - **Azure Data Studio** features and capabilities
  - Managing SQL data in Azure
  - Creating and using **SQL Notebooks**
- Ideal for those who want to use **modern, cross-platform tools**

---

## 📦 **Non-Relational Data Concepts**

### 🧾 **Why Non-Relational Data?**

- Relational databases require a **predefined schema**, which may not be suitable when:
  - Data structure is **unknown in advance**
  - Data comes from **diverse sources** (e.g., mobile apps, IoT, social media)
  - **High ingestion speed** is needed
  - Data is **unstructured** (e.g., images, audio, video)

### 🧪 **Use Cases**

- **IoT and telematics**
- **Gaming**
- **Web and mobile apps**
- **Social networks**

---

## 🧱 **Types of Non-Relational Data**

### 1️⃣ **Unstructured Data**

- No defined schema or searchable fields
- Examples:
  - **Images**
  - **Videos**
  - **Audio files**
- Storage options:
  - **Azure Files**
  - **Azure Blob Storage**

---

### 2️⃣ **Semi-Structured Data**

- Contains fields, but schema is **flexible**
- Fields may **vary across records**
- Can be stored in:
  - **Non-relational databases**
  - **Files** (for ingestion and processing)

---

## 📄 **Popular Non-Relational File Formats**

| Format      | Description                                                        |
| ----------- | ------------------------------------------------------------------ |
| **JSON**    | Most popular; used across Azure, Dynamics, Office 365              |
| **Parquet** | Columnar format; high compression; developed by Cloudera & Twitter |
| **ORC**     | Optimized Row Columnar; used in Apache Hive                        |
| **Avro**    | Row-based format; JSON header + binary body; great for compression |

---

### 🧠 **Why Use These Formats?**

- Efficient for **data ingestion and processing**
- Often used in **staging layers** before moving data to relational databases

---

## 🗃️ **Non-Relational Database Offerings in Azure**

Also known as **NoSQL databases**, these are designed for **flexible, high-speed data storage** and retrieval, especially when data structure is **not fixed** or **highly variable**.

---

### 🧩 **Types of NoSQL Databases**

---

### 1️⃣ **Key-Value Stores**

#### 📌 Overview

- Simplest and fastest NoSQL type
- Each item is stored as a **key-value pair**
- Schema is **flexible**; rows can have any number of columns

#### ⚡ Use Case

- **Fast ingestion** of large volumes of data

#### ❌ Limitations

- Can only **search by key**
- No in-place updates; must **retrieve → modify → overwrite**

#### 🧳 Azure Options

- **Azure Table Storage**
- **Cosmos DB (Table API)**

---

### 2️⃣ **Document Databases**

#### 📌 Overview

- Stores data in **document format** (usually **JSON**)
- Schema is **flexible** per document
- Supports **queries on both keys and values**
- Allows **in-place updates** and **indexing**

#### 📦 Example

- A single JSON document might contain:
  - Order details
  - Product list
  - Customer contact info  
    → Would require **multiple joins** in a relational DB

#### ⚠️ Trade-offs

- **Data repetition** (e.g., customer info repeated across orders)
- **Slower than key-value**, but **faster than relational databases**

#### 🧳 Azure Option

- **Cosmos DB (SQL API)**

---

### 3️⃣ **Column-Family Databases**

#### 📌 Overview

- Similar to relational DBs but focused on **columns**, not rows
- Groups related columns into **column families**
  - Example:
    - Customer Info: Title, First Name, Last Name
    - Address Info: Street, City, ZIP

#### 📈 Benefits

- **Faster retrieval** of grouped data
- Ideal for **column-based queries**

#### 📄 Related Formats

- **ORC**, **Parquet** (columnar file formats)

#### 🧳 Azure Option

- **Cosmos DB (Cassandra API)**

---

### 4️⃣ **Graph Databases**

#### 📌 Overview

- Designed to store and query **complex relationships**
- Data is modeled as:
  - **Nodes** (entities)
  - **Edges** (relationships)

#### 🔄 Example

- Node types: Person, Country, Company
- Edges:
  - Luis → Citizen of → Mexico
  - Luis → Works at → Microsoft

#### 📈 Benefits

- Efficient for **relationship traversal**
- **Faster than relational joins** for complex queries

#### 🧳 Azure Option

- **Cosmos DB (Gremlin API)**

---

## 🌐 **Azure Cosmos DB Overview**

### 📌 What is Cosmos DB?

- **Microsoft’s primary NoSQL database platform**
- Operates at **PaaS (Platform as a Service)** level
- Stores data as **JSON documents**
- Supports **multiple NoSQL models** via different APIs

---

## ⚡ **Key Features**

- **Multi-model support**:
  - Document
  - Key-value
  - Column-family
  - Graph
- **Ultra-low latency**:
  - <10 ms for reads and writes (99% of the time)
- **Global scalability**:
  - Data partitioned across multiple nodes
- **High availability**:
  - 99.99% SLA
- **Security**:
  - Data encrypted **at rest** and **in transit**
  - Compliant with strict security standards

---

## 🧳 **Use Cases**

- **IoT and telematics**
- **Gaming**
- **Mobile and web apps**
- Used internally by Microsoft for:
  - **Skype**
  - **Xbox**
  - **Office 365**
  - **Azure services**

---

## 🔌 **Cosmos DB APIs (Data Models)**

| API               | Purpose / Use Case                                                       |
| ----------------- | ------------------------------------------------------------------------ |
| **SQL API**       | Default for new document-based projects; supports SQL-like queries       |
| **Gremlin API**   | For graph databases; supports graph traversal queries                    |
| **Table API**     | For key-value stores; migration from Azure Table Storage                 |
| **MongoDB API**   | For document databases; migration from MongoDB with minimal code changes |
| **Cassandra API** | For column-family databases; migration from Apache Cassandra             |

---

## 🗂️ **Cosmos DB Structure**

### 🔹 Hierarchy

1. **Cosmos DB Account**  
   → Up to 50 per Azure subscription
2. **Databases**  
   → One or more per account
3. **Containers**  
   → Unit of **scalability** for throughput & storage  
   → Varies by API (e.g., Graph for Gremlin API)
4. **Items**  
   → Actual data (e.g., documents, nodes, edges)  
   → Can include small binary files (up to 2 MB)  
   → Larger files can be stored in **Azure Blob Storage**

---

## ⚙️ **Management Tasks**

### 🛠️ Provisioning

- Can be done via:
  - **Azure Portal**
  - **Azure CLI**
  - **Azure PowerShell**
  - **ARM Templates**
- Requires setting **Request Units (RUs)**:
  - Minimum: **400 RUs/sec**
  - RUs = billing + performance unit
  - Can be configured at **database** or **container** level

### 🔁 Replication

- **Automatic** within a region
- Supports **multi-master replication** for global write access

---

## 🔍 **Querying & Migration Tools**

### 📊 Querying

- Use **Data Explorer** in Azure Portal

### 🔄 Migration

- Use **Cosmos DB Data Migration Tool** (available on GitHub)

---

## 🗄️ **Azure Storage Overview**

Azure Storage is a **collection of services** under one umbrella, all accessible via a single **Azure Storage Account**.

### 📦 Services Included:

- **Azure Blob Storage**
- **Azure Files**
- **Azure Table Storage**
- **Azure Queues** _(not covered in DP-900 exam)_

---

## 🔑 **Azure Table Storage**

### 📌 Key Features

- **Key-value store** (NoSQL)
- No schema, relationships, stored procedures, or foreign keys
- **Search only by key**, not by value

### ⚡ Performance

- **Fast data ingestion and retrieval**
- Supports **partitioning** for performance optimization
  - Choosing a good **partition key** is critical

### 📈 Scalability

- Can store **hundreds of terabytes**
- Supports **multiple read replicas**
- ❌ Does **not** support multiple write regions

### 🧳 Use Cases

- **IoT and telematics**
- High-throughput, low-complexity data storage

---

## 🧱 **Azure Blob Storage**

### 📌 What is a Blob?

- **Binary Large Object** – used for **unstructured data**

### 📦 Features

- Stores **massive amounts of data** + **metadata**
- Example: Store medical images (X-rays, MRIs) with patient info

### 🔐 Security

- Supports **encryption**
  - Includes **Bring Your Own Key (BYOK)** option

### 🧊 Access Tiers

| Tier        | Description                                                                      |
| ----------- | -------------------------------------------------------------------------------- |
| **Hot**     | High performance, higher cost – for frequently accessed data                     |
| **Cool**    | Lower cost, moderate performance – for infrequent access                         |
| **Archive** | Lowest cost, slowest access – for long-term storage (rehydration may take hours) |

### 🧳 Use Cases

- Hosting images/documents for websites
- Streaming audio/video
- Backups and archives
- Storing data for analytics

---

## 📁 **Azure Files**

### 📌 Overview

- Cloud-based **file shares** accessible over the internet

### 🔗 Protocol Support

- **SMB 3.0** (Windows)
- **NFS** _(Linux – currently in preview)_

### 🔐 Security

- Supports **encryption**, **BYOK**, and **Azure AD integration**

### ⚙️ Performance Tiers

| Tier         | Description                                |
| ------------ | ------------------------------------------ |
| **Standard** | Uses HDD – lower cost, lower performance   |
| **Premium**  | Uses SSD – higher cost, better performance |

### 🧳 Use Case

- **Migration of file shares** from on-premises Windows servers
- Use **AzCopy** command-line tool for cloud migration

---

## 🧪 **Working with Non-Relational Databases in Azure**

This demo walks through the process of creating an **Azure Storage Account** and setting up **Blob Storage**, which is used for storing **unstructured data**.

---

### 🛠️ **Creating an Azure Storage Account**

#### 📌 Steps:

1. Go to **Azure Portal**
2. Click **Create a Resource**
3. Search for **Storage Account**
4. Click **Create**

#### 🧾 Configuration:

- **Resource Group**: `LinkedInLearning`
- **Storage Account Name**: `dp900blobstorage`
- **Region**: `Southeast Asia` (closest data center)
- **Performance Tier**: `Standard`
- **Replication**: `Locally Redundant Storage (LRS)` – cost-effective for labs

---

### ⚙️ **Advanced Settings**

- **Hierarchical Namespace**:
  - Used for **Azure Data Lake Storage**
  - Not enabled in this demo

---

### 📂 **Navigating the Storage Account**

Once created, the storage account includes:

| Section         | Purpose                              |
| --------------- | ------------------------------------ |
| **Containers**  | Blob Storage (unstructured data)     |
| **File Shares** | Azure Files                          |
| **Tables**      | Azure Table Storage                  |
| **Queues**      | Azure Queues _(not covered in exam)_ |

---

### 📁 **Creating a Blob Container**

- Navigate to **Containers**
- Click **Create New Container**
- Name: `dp900`
- Container acts like a **folder** for storing files
- Once created, you can **upload files** into it

---

## 📚 **Additional Resources for Non-Relational Databases**

If you'd like to go deeper into **coding**, **implementation**, and **tool usage** for non-relational data in Azure, here are some recommended learning resources:

---

### 🧠 **Microsoft Learn**

- Official Microsoft platform for **interactive tutorials**
- Includes **exam-specific study paths** for **DP-900**
- Covers:
  - Cosmos DB
  - Azure Storage (Blobs, Tables, Files)
  - NoSQL data models

---

### 📘 **LinkedIn Learning Courses**

#### 1️⃣ **Azure Storage for Developers – by Anton Delsink**

- Covers:
  - **Azure Files**
  - **Azure Blobs**
  - **Azure Tables**
  - **Azure Queues**
- Great for understanding **storage services from a developer’s perspective**

#### 2️⃣ **Azure for Developers: Cosmos DB – by Sidney Andrews**

- Focuses on:
  - **Cosmos DB architecture**
  - **APIs and data models**
  - **Use cases and performance tuning**

#### 3️⃣ **Azure Cosmos DB: SQL API Deep Dive – by Sidney Andrews**

- Explores:
  - **SQL API in Cosmos DB**
  - **Querying JSON documents**
  - **Advanced features like indexing and partitioning**

---

## 📊 **Understanding Analytics Workloads**

Analytics workloads help transform raw data into **valuable business insights**. These workloads are typically categorized into two main types:

---

### 🧾 **1. OLTP – Online Transaction Processing**

#### 📌 Purpose

- Supports **day-to-day business operations**
- Handles **small, discrete transactions** (e.g., banking, retail)

#### 🔄 Example

- Transferring money between accounts:
  - Must **subtract** from one and **add** to another **as a single unit**

#### ✅ Key Properties (ACID)

| Property        | Description                                         |
| --------------- | --------------------------------------------------- |
| **Atomicity**   | All parts of a transaction succeed or fail together |
| **Consistency** | Data remains valid before and after the transaction |
| **Isolation**   | Transactions don’t interfere with each other        |
| **Durability**  | Once committed, data is permanently saved           |

#### ⚙️ Characteristics

- **High volume** of transactions
- Optimized for **CRUD operations** (Create, Read, Update, Delete)
- Typically uses **relational databases**:
  - SQL Server, Oracle, DB2

---

### 📈 **2. OLAP – Online Analytical Processing**

#### 📌 Purpose

- Supports **Business Intelligence (BI)** and **decision-making**
- Focuses on **read-intensive operations**

#### 🔍 Example

- Aggregating millions of sales records to calculate **annual revenue**

#### ⚙️ Characteristics

- Optimized for **reporting and analysis**
- Less focus on updates/deletes
- Data often sourced from **OLTP systems**
- Common tools:
  - **SQL Server Analysis Services**
  - **Azure Synapse Analytics**

---

## 🧱 **Data Modeling for OLTP vs. OLAP**

### 🔄 OLTP: **Normalized Data**

- Data is split across **related tables**
- Reduces **redundancy**, improves **data integrity**
- Example:
  - Customer email → stored in **Customers table**
  - Product color → stored in **Products table**

### 📊 OLAP: **De-normalized Data**

- Combines data into **fewer tables** for faster reads
- Accepts **some redundancy** to reduce joins
- Ideal for **reporting and analytics**

---

## 🌟 **Star Schema vs. Snowflake Schema**

### ⭐ **Star Schema**

- Central **Fact Table** (e.g., sales, transactions)
- Connected to multiple **Dimension Tables** (e.g., customer, product)
- Simple structure, easy to understand

### ❄️ **Snowflake Schema**

- Dimensions are **normalized**
- Reduces data repetition
- More complex, but saves **storage space**
- May reduce **query performance**

---

## 🏢 **Modern Data Warehousing Overview**

Modern data warehouses go beyond traditional OLAP systems. They integrate data from **multiple sources**, support **varied formats**, and enable **real-time analytics**.

---

### 🔄 **Evolution of Data Warehousing**

- Traditional warehouses reorganized **OLTP data** for reporting.
- Modern warehouses ingest data from:
  - **IoT devices**
  - **Social networks**
  - **Web APIs**
  - **Files**
  - **Enterprise systems** (CRM, HR, ERP)

#### 📊 Value of Integration

- Cross-referencing data across systems reveals deeper insights:
  - Impact of a **social media campaign** on sales
  - Effect of an **HR policy** on productivity

---

## 📁 **Data Format Diversity**

- Modern warehouses must handle:
  - **CSV**, **XML**, **JSON**
  - **Parquet**, **ORC**
  - **Audio**, **Video**, **Images**
- Can use **Cognitive Services** to:
  - Extract text from audio
  - Analyze image metadata

---

## 🚀 **Real-Time & Big Data Support**

- Data may arrive via:
  - **Batch (ETL/ELT)**
  - **Streaming** (e.g., sensors, stock feeds)
- Must support **Big Data**:
  - High **volume**, **velocity**, and **variety**

---

## 🧱 **Phases of a Modern Data Warehouse**

### 1️⃣ **Data Ingestion**

- Capturing data from various sources
- Azure tools:
  - **Azure Data Factory**
  - **Stream Analytics**
  - **Event Hubs**

#### 🧊 Staging Layer

- Temporarily holds fast-arriving data
- Useful for **batching** or **on-the-fly analysis**
- Can use **Azure Data Lake** to store raw data

---

### 2️⃣ **Data Transformation & Processing**

- Cleansing, filtering, normalization/denormalization
- Format conversion
- Azure tools:
  - **Azure Data Factory**
  - **Azure Databricks**

---

### 3️⃣ **Data Modeling & Serving**

- Structuring data for **reporting and BI**
- Azure tools:
  - **Azure Analysis Services**
  - **Azure Synapse Analytics**

---

### 4️⃣ **Visualization Layer**

- Creating **interactive reports and dashboards**
- Tool of choice: **Power BI**

---

## 🔄 **Understanding Data Ingestion Components**

Microsoft offers several tools for **data ingestion**, **transformation**, and **staging** in modern data workflows. These tools support both **ETL** (Extract, Transform, Load) and **ELT** (Extract, Load, Transform) processes.

---

### 🛠️ **Azure Data Factory (ADF)**

#### 📌 Overview

- **Cloud-based**, fully managed **data integration and orchestration** service
- Ideal for **data engineers**
- Supports **on-premises** and **cloud** sources

#### 🔗 Supported Sources

- Azure services
- Competitor clouds (AWS, Google Cloud)
- Relational & non-relational databases (SQL Server, Oracle, MongoDB, Cassandra, SAP HANA)
- SaaS apps (Dynamics, Jira, Salesforce)
- File formats: **JSON**, **XML**, **Parquet**, **Avro**, **ORC**

#### ⚙️ Capabilities

- Ingests large volumes of raw data
- Cleans, transforms, restructures data
- Supports **ETL** and **ELT**
- Can call external services (e.g., **Databricks**, **HDInsight**) for transformations

---

### 🧱 **ADF Core Components**

| Component               | Description                                               |
| ----------------------- | --------------------------------------------------------- |
| **Pipeline**            | Logical group of activities (like a spreadsheet in Excel) |
| **Activities**          | Individual steps in a pipeline                            |
| → Data Movement         | Moves data from source to destination (sink)              |
| → Data Transformation   | Changes data (via ADF or external compute)                |
| → Control Flow          | Implements logic (loops, conditions, triggers)            |
| **Integration Runtime** | Compute infrastructure for executing activities           |
| **Linked Services**     | Connection info for data sources or compute resources     |
| **Datasets**            | Metadata and structure of the data (e.g., JSON, XML)      |
| **Triggers**            | Initiates pipeline execution (time-based or event-based)  |

---

### 🖥️ **Other Microsoft ETL Tools**

#### 1️⃣ **SSIS – SQL Server Integration Services**

- **On-premises** ETL tool
- More transformation options than ADF (currently)
- Limited scalability (depends on server performance)
- Can be migrated to Azure via **ADF integration**

#### 2️⃣ **PolyBase**

- Feature in **SQL Server** and **Azure Synapse Analytics**
- Allows querying external data sources (e.g., Azure Data Lake, Blob Storage, Hadoop) using **T-SQL**
- Supported by ADF
- Not available in **Azure SQL Database**

---

## 🌊 **Azure Data Lake**

### 📌 Purpose

- Stores **large volumes of raw data**
- Used as a **staging layer** before loading into a data warehouse

### 🧱 Components

| Component                     | Description                                 |
| ----------------------------- | ------------------------------------------- |
| **Azure Data Lake Storage**   | File repository for semi/unstructured data  |
| **Azure Data Lake Analytics** | On-demand analytics service using **U-SQL** |

### 🔐 Features

- Compatible with **HDFS**
- Accessible by ADF, Databricks, HDInsight, Stream Analytics
- **Gen2** version is a superset of Blob Storage
- Supports **RBAC** at folder/file level
- Enables **hierarchical namespace** (folders & subfolders)

---

## 📊 **Understanding Data Analytics Tools in Azure**

Once data is ingested, transformed, and staged, **analytics tools** help extract **valuable insights**. Azure offers several powerful platforms for this purpose.

---

### 🧠 **1. Azure Databricks**

#### 📌 Overview

- **Advanced analytics & machine learning platform**
- Based on **Apache Spark** (parallel processing engine)
- Designed for **large-scale data analysis**

#### ⚙️ Features

- **Distributed computing** across clusters → faster processing
- **Collaborative workspace** for:
  - Data engineers
  - Data scientists
  - Business analysts
- Uses **notebooks**:
  - Mix of **code**, **visualizations**, and **text**
  - Supports multiple languages: **Python**, **R**, **Scala**, **Java**, **SQL**
- Supports **stream processing**
- Integrates with:
  - Azure Data Lake
  - SQL databases
  - Cosmos DB
  - Azure Data Factory (via Databricks activities)

---

### 🧠 **2. Azure HDInsight**

#### 📌 Overview

- **Managed analytics service** based on **Apache Hadoop**
- Processes large data sets using **clusters**

#### ⚙️ Supported Frameworks

- Hadoop
- MapReduce
- Spark
- Hive
- Kafka
- Storm
- R

#### 📦 Storage

- Uses **Azure Data Lake Storage**
- Integrates with other Azure services

---

### 🧱 **3. Azure Analysis Services**

#### 📌 Overview

- Builds **tabular models** for **OLAP queries**
- Focused on **analytics**, not transactions

#### ⚙️ Features

- Combines data from multiple sources
- Optimized for **Business Intelligence (BI)**
- Includes **graphical designer** for:
  - Filtering
  - Aggregation
  - Query building
- Supports **DAX** (Data Analysis Expressions) language

---

### 🧠 **4. Azure Synapse Analytics**

#### 📌 Overview

- Combines **big data analytics** and **data warehousing**
- Based on **Spark** and **notebooks**

#### ⚙️ Features

- Supports multiple languages:
  - **PolyBase**, **C#**, **Python**, **Scala**, **Spark SQL**
- Supports multiple file formats:
  - **CSV**, **JSON**, **XML**, **Parquet**, **ORC**, **Avro**
- Includes:
  - **Synapse Pipelines** (based on Azure Data Factory)
  - **Synapse Link for Cosmos DB** → supports **HTAP** (Hybrid Transactional/Analytical Processing)
  - **Synapse Studio** → web interface for managing SQL & Spark code

#### ⚡ Scalability

- Uses **Massively Parallel Processing (MPP)** engine:
  - **Control node** (brain)
  - **Compute nodes** (processing power)
- Two compute modes:
  - **SQL Pools** (up to 60 nodes)
  - **Spark Pools**
- Supports **autoscaling** and **pause during idle** to reduce costs

---

## ⚖️ **Azure Analysis Services vs. Azure Synapse Analytics**

| Feature                       | Azure Synapse Analytics     | Azure Analysis Services                 |
| ----------------------------- | --------------------------- | --------------------------------------- |
| **Best for**                  | Large datasets, complex ELT | Smaller datasets, high read concurrency |
| **Scalability**               | High (MPP engine)           | Moderate                                |
| **Concurrency**               | Moderate                    | High (thousands of users)               |
| **Integration with Power BI** | Good                        | Excellent                               |
| **Development Experience**    | Complex                     | Easier                                  |
| **Common Use**                | Heavy lifting               | Serving business users                  |

✅ **Often used together**:

- Synapse for **processing & modeling**
- Analysis Services for **serving BI users**

---

## 📊 **Introduction to Power BI**

Power BI is Microsoft’s leading **data visualization and business intelligence tool**, designed to turn raw data into **interactive reports and dashboards**.

---

### 🎨 **What is Data Visualization?**

- Graphical representation of data using:
  - **Charts** (bar, column, line, pie, donut)
  - **Tables & matrices**
  - **Maps** (geographic data)
- Helps identify:
  - **Trends**
  - **Anomalies**
  - **Patterns**

---

## 🧰 **Power BI Components**

| Component                  | Description                                                      |
| -------------------------- | ---------------------------------------------------------------- |
| **Power BI Desktop**       | Create reports locally                                           |
| **Power BI Pro (Service)** | Cloud-based platform for sharing and viewing reports             |
| **Power BI Mobile**        | View reports on mobile devices                                   |
| **Other Tools**            | Gateway, Report Server, Embedded, Premium (less focus in DP-900) |

---

### 🔗 **Data Connectivity**

- Connects to **130+ data sources**:
  - Files
  - Databases
  - Data warehouses
  - SaaS applications
- Combines multiple sources into a **single data model**

---

## 🧱 **Power BI Workflow & Key Concepts**

### 1️⃣ **Dataset**

- Collection of data used to build reports
- Created using:
  - **Power Query** (in Desktop)
  - **Dataflows** (in Service)

### 2️⃣ **Visualizations (Visuals)**

- Graphical elements like:
  - Bar, line, pie charts
  - Tables, matrices
  - Maps
- Power BI includes **24 built-in visuals**
- **300+ additional visuals** available via **AppSource**

### 3️⃣ **Report**

- Collection of visuals grouped into **pages**
- Created in **Power BI Desktop**
- Published to **Power BI Service**

### 4️⃣ **Dashboard**

- **Single-page** summary view
- Combines visuals from **multiple reports**
- Cannot be filtered or drilled down like reports
- Can include **dynamic elements** (images, text, web content)

### 5️⃣ **App**

- Package of dashboards and reports
- Used by **large organizations** or **software vendors** to distribute content

---

## 🔍 **Reports vs. Dashboards**

| Feature           | Report              | Dashboard                    |
| ----------------- | ------------------- | ---------------------------- |
| **Pages**         | Multiple            | Single                       |
| **Interactivity** | Filter & drill down | No filtering or drill down   |
| **Source**        | One dataset         | Can combine multiple reports |
| **Use Case**      | Detailed analysis   | High-level overview          |

---

## 🧪 **Demo: Data Warehousing on Microsoft Azure**

This demo shows how to use **Azure Data Factory** to create a pipeline that **transfers data from an Azure SQL Database to Azure Blob Storage**, and then visualize it using **Power BI**.

---

### 🛠️ **Step 1: Create Azure Data Factory**

#### 📌 Configuration

- **Resource Name**: `DP900ADF`
- **Region**: Southeast Asia
- **Version**: V2
- **Git Configuration**: Skipped
- **Networking**: Default settings

---

### 🔄 **Step 2: Create a Pipeline Using Copy Data Wizard**

#### 📌 Source Configuration

- **Source Type**: Azure SQL Database
- **Detected Automatically** by Data Factory
- Provide:
  - **Username & Password**
  - **Database Name**
- Select **Products Table** for export

#### 📌 Destination Configuration

- **Destination Type**: Azure Blob Storage
- **Detected Automatically**
- Select **Container Path**
- Optionally set **file name**
- Review summary → **Copy data**

---

### 📁 **Step 3: Verify Data in Blob Storage**

- Navigate to **Blob Storage Resource**
- Open **Containers**
- Locate the **exported file** (Products table)
- Confirm data is successfully copied

---

## 📊 **Step 4: Visualize Data in Power BI**

### 🖥️ Power BI Desktop

- Open existing report or create a new one
- Add visuals:
  - **Map View**: Revenue by state
  - Example: Texas and California outperform New York

### 📤 Publish Report

- Click **Publish**
- Opens **Power BI App Interface**

---

### 📈 Power BI Features Demonstrated

| Feature                      | Description                                                            |
| ---------------------------- | ---------------------------------------------------------------------- |
| **Interactive Reports**      | Click filters visuals dynamically                                      |
| **Dashboards**               | Combine visuals from multiple reports into one page                    |
| **Natural Language Queries** | Ask questions like “Total sales per…” and get dynamic visual responses |

---

## 📚 **Additional Resources for Modern Data Warehousing & Analytics**

If you'd like to **go deeper** into the concepts covered in the course or prepare more thoroughly for the **DP-900 exam**, here are some recommended resources:

---

### 🧠 **Microsoft Learn**

- **Official learning platform** from Microsoft
- Includes:
  - **DP-900 exam-specific study paths**
  - Tutorials on **Power BI**, **Azure Synapse**, **Data Factory**, and more
- Ideal for **conceptual understanding** and **hands-on practice**

---

### 📘 **LinkedIn Learning Courses**

#### 1️⃣ **Azure Spark Databricks Essential Training**

- Covers:
  - **Databricks architecture**
  - **Notebooks**
  - **Spark-based analytics**
- Great for understanding **real-world implementation**

#### 2️⃣ **Microsoft Azure Synapse for Developers**

- Focuses on:
  - **Synapse Studio**
  - **SQL & Spark pools**
  - **Data modeling and serving**
- Ideal for **developers and data engineers**

---

### 🎓 **Power BI Learning Resources**

- Microsoft Learn offers **step-by-step guides** for:
  - Creating reports and dashboards
  - Using **Power BI Desktop**, **Pro**, and **Mobile**
  - Connecting to various data sources

---

### 💬 Final Note from Instructor

- Re-watch videos if needed
- Use the resources for **different perspectives**
- Reach out on **LinkedIn** to celebrate your certification success
