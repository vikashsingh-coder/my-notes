<!-- Give me the detailed summary of given transcript, so that this generated notes will be suffient for my revision and explanation,
- you can inclued your example
- language should be easy  to understood
- try to add example if applicable for sql (help to understood concept) -->

Here’s a **detailed and easy-to-understand summary** of the **Intro and Course Overview** section from the Snowflake training transcript. I’ve also added examples and simplified explanations to help you revise and explain the concepts better.

---

## 🧠 **Course Introduction Summary (Simplified for Revision)**

### 🎓 **Course Name**:

**Intro to Snowflake for Data Engineers, Data Scientists, and App Developers**

### 👨‍🏫 **Instructor**:

Peter Olson – Developer Advocate at Snowflake

---

## 📌 **What is Snowflake?**

### ✅ **Simple Definition**:

Snowflake is a **Data Cloud** – a global platform where companies can store, manage, and analyze data with **high speed, scalability, and collaboration**.

### ✅ **Two Main Parts**:

1. **Platform** – The engine that runs Snowflake (you’ll learn how to use this).
2. **Data** – The actual information stored and shared.

### 🧠 **Think of it like this**:

Imagine Snowflake as a **giant library**:

- The **platform** is the building, shelves, and staff.
- The **data** is the books and documents.
- You can read, write, share, and even build apps using this library.

---

## 👥 **Who is this course for?**

This course is designed for:

- **Data Engineers**
- **Data Scientists**
- **App Developers**
- **ML Engineers**

### ✅ **Common Goal**:

To learn **foundational Snowflake skills** for career growth.

### ✅ **Builder Concept**:

Snowflake calls these learners **builders** because they:

- Build data pipelines
- Build ML models
- Build data apps

### 🧠 **Example**:

A data scientist might use SQL to clean data and Python to build a prediction model. In Snowflake, they can do both in one place.

---

## 🧠 **What You Should Know Before Starting**

You should be **familiar with basic SQL and Python**.

### ✅ **SQL Example**:

```sql
SELECT * FROM employees
WHERE department = 'Sales'
ORDER BY salary DESC;
```

### ✅ **Python Example**:

```python
import pandas as pd

df = pd.read_csv("data.csv")
df.head()
```

If you're not comfortable with these, it's better to take a beginner course first.

---

## 🎯 **Course Goals**

### 🥇 **Main Goal**:

Even if this is the only Snowflake course you take, you should learn:

1. **Core Objects** – Tables, Views, Schemas, etc.
2. **Architecture** – How Snowflake is built and works.
3. **Key Features** – Like Time Travel, UDFs (User Defined Functions).
4. **Use Cases** – Data Engineering, ML, AI, App Development.

### 🧠 **Example – Time Travel**:

Snowflake lets you **go back in time** to recover deleted or changed data.  
Like an "Undo" button for your database.

---

## 🧭 **What’s Covered in Part 1 of the Course?**

You’ll learn about:

- **Virtual Warehouses** – Compute power (like engines).
- **Stages** – Temporary storage areas.
- **Databases & Schemas** – Data organization.
- **Tables & Views** – Where data lives and how it's seen.
- **Semi-Structured Data** – JSON, XML, etc.
- **Architecture Layers** – How Snowflake is built internally.

---

## ✅ **Quick Recap for Revision**

| Topic                | Simple Explanation   | Example                           |
| -------------------- | -------------------- | --------------------------------- |
| Snowflake            | Data Cloud platform  | Like Google Drive for data        |
| Builder              | Data role merging    | Data scientist using SQL & Python |
| SQL                  | Query language       | `SELECT * FROM table`             |
| Python               | Programming language | `df.head()`                       |
| Time Travel          | Undo changes         | Recover deleted rows              |
| Virtual Warehouse    | Compute engine       | Like CPU for Snowflake            |
| Schema               | Data structure       | Folder inside a database          |
| Semi-Structured Data | Flexible format      | JSON, XML                         |

---

Would you like me to create **flashcards**, **quiz questions**, or a **diagram** to help you revise this better?

Here’s a **detailed and simplified summary** of the **“Worksheets and a Simple Example”** section from the Snowflake course. I’ve also added a **realistic SQL example** and explanations to help you understand and revise better.

---

## 🧠 **Part 1: Worksheets and a Simple Example – Summary for Revision**

### 🎯 **Goal of This Section**:

To **start using Snowflake** by uploading a SQL worksheet and running your **first query** on a sample dataset called **Tasty Bytes**.

---

## 🧑‍💻 **How You Interact with Snowflake**

### ✅ **Main Interface**:

**Snowsight** – Snowflake’s browser-based UI where you write and run SQL or Python code.

### ✅ **Worksheets**:

- You can create **SQL worksheets** to run queries.
- You can also use **Python worksheets** or **Snowflake-native notebooks**.

---

## 📁 **Dataset Used: Tasty Bytes**

- A **fictional food truck company** with 450 trucks in countries like India, Japan, France, etc.
- This dataset is used throughout the course for practice.

---

## 🧪 **Steps to Start Querying Data**

### ✅ Step-by-step Actions (Simplified):

1. **Upload SQL Worksheet**

   - Go to **Projects > Worksheets**
   - Click **Create Worksheet from SQL File**
   - Select your `.sql` file

2. **Understand Comments in SQL**

   - **Block comment**: `/* This is a block comment */`
   - **Line comment**: `-- This is a single-line comment`

3. **Run SQL Code Blocks**

   - Use **Command + Enter** (Mac) or **Ctrl + Enter** (PC) to run a block of code.

4. **Set Role and Warehouse**

   - Example:
     ```sql
     USE ROLE SYSADMIN;
     USE WAREHOUSE COMPUTE_WH;
     ```

5. **Create Database, Schema, Table, and Load Data**

   - Example:
     ```sql
     CREATE DATABASE tasty_bytes_sample_data;
     CREATE SCHEMA raw_pos;
     CREATE TABLE menu (...);
     -- Load data from stage (S3 bucket)
     ```

6. **Run First Query**
   - Example:
     ```sql
     SELECT COUNT(*) AS row_count
     FROM tasty_bytes_sample_data.raw_pos.menu;
     ```
   - ✅ Output: `100 rows` – You’ve successfully queried your first table!

---

## 🧠 **Realistic SQL Example Explained**

Let’s break down the query:

```sql
SELECT COUNT(*) AS row_count
FROM tasty_bytes_sample_data.raw_pos.menu;
```

### 🔍 What it does:

- `COUNT(*)`: Counts all rows in the table.
- `AS row_count`: Gives a name to the output column.
- `FROM tasty_bytes_sample_data.raw_pos.menu`: Specifies the table path:
  - `Database`: `tasty_bytes_sample_data`
  - `Schema`: `raw_pos`
  - `Table`: `menu`

### 🧠 Think of it like:

> “How many items are listed in the food truck menu?”

---

## ✅ **Quick Recap Table**

| Concept   | Explanation        | Example                      |
| --------- | ------------------ | ---------------------------- |
| Snowsight | Snowflake's web UI | Like Google Docs for SQL     |
| Worksheet | Place to write SQL | SQL worksheet with queries   |
| Role      | Access level       | `USE ROLE SYSADMIN;`         |
| Warehouse | Compute engine     | `USE WAREHOUSE COMPUTE_WH;`  |
| Stage     | Temporary storage  | Load data from S3            |
| Table     | Data container     | `menu` table                 |
| Query     | SQL command        | `SELECT COUNT(*) FROM menu;` |

---

Would you like me to create a **practice worksheet**, **SQL cheat sheet**, or a **step-by-step guide** to set up your own Snowflake environment?

Here’s a **detailed and easy-to-understand summary** of **“Worksheets and a Simple Example: Part 2”** from the Snowflake course, along with **SQL examples** and explanations to help you revise and explain the concepts confidently.

---

## 🧠 **Part 2 Summary – Exploring the Tasty Bytes Dataset**

### 🎯 **Goal of This Section**:

To **explore the dataset** further using SQL queries and understand how to analyze structured and semi-structured data in Snowflake.

---

## 🔍 **Step-by-Step Exploration**

### ✅ 1. **View Sample Data**

```sql
SELECT TOP 10 *
FROM tasty_bytes_sample_data.raw_pos.menu;
```

- **Purpose**: Shows the first 10 rows of the `menu` table.
- **Observation**: Contains desserts, beverages, cost price, selling price, ingredients, and health info.
- **Note**: Some columns contain **semi-structured data** (like JSON) – we’ll learn more about this later.

---

### ✅ 2. **Count Food Truck Brands**

```sql
SELECT TRUCK_BRAND_NAME, COUNT(*)
FROM tasty_bytes_sample_data.raw_pos.menu
GROUP BY 1
ORDER BY 2 DESC;
```

- **GROUP BY 1**: Groups by the first column (`TRUCK_BRAND_NAME`)
- **ORDER BY 2 DESC**: Sorts by the second column (count), highest to lowest

🧠 **Result**:

- There are **15 different food truck brands**
- Each brand has **6 to 10 menu items**

---

### ✅ 3. **Explore Relationship Between Brand and Menu Type**

```sql
SELECT TRUCK_BRAND_NAME, MENU_TYPE, COUNT(*)
FROM tasty_bytes_sample_data.raw_pos.menu
GROUP BY 1, 2
ORDER BY 3 DESC;
```

- **GROUP BY 1, 2**: Groups by both `TRUCK_BRAND_NAME` and `MENU_TYPE`
- **ORDER BY 3 DESC**: Sorts by count

🧠 **Insight**:

- Each brand has a unique menu type
- There’s a **one-to-one mapping** between `TRUCK_BRAND_NAME` and `MENU_TYPE`

---

## 🧑‍💻 **Working with Worksheets in Snowsight**

### ✅ Create a New Worksheet:

- Click the **plus (+)** icon at the top or in the Worksheets section
- Paste and run SQL code like:

```sql
SELECT COUNT(*) AS row_count
FROM tasty_bytes_sample_data.raw_pos.menu;
```

### ✅ Rename Worksheet:

- Click the **three vertical dots** at the top of the worksheet tab
- Rename it (e.g., “Beautiful Blank Worksheet – So Much Possibility”)

---

## 🧠 **Quick Recap Table**

| Concept           | Explanation             | SQL Example                  |
| ----------------- | ----------------------- | ---------------------------- |
| `SELECT TOP 10 *` | View sample rows        | `SELECT TOP 10 * FROM menu;` |
| `GROUP BY`        | Group data by column    | `GROUP BY TRUCK_BRAND_NAME`  |
| `ORDER BY DESC`   | Sort results            | `ORDER BY COUNT(*) DESC`     |
| `MENU_TYPE`       | Type of menu            | Dessert, Beverage, etc.      |
| Worksheet         | SQL editor in Snowsight | Create, rename, run queries  |

---

## 🧪 **Practice Tip**:

Try modifying the queries:

- Find **average selling price** per brand
- Count **items per menu type**
- Extract **ingredients** from semi-structured columns (later in the course)

Would you like me to create a **practice worksheet**, **SQL exercises**, or a **mini project** based on this dataset to help you revise better?

Here’s a **detailed and easy-to-understand summary** of the **“Virtual Warehouses Overview”** section from the Snowflake course, with **realistic examples** and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Virtual Warehouses in Snowflake – Summary for Revision**

### 🎯 **Goal of This Section**:

To understand what **virtual warehouses** are, how to **create**, **use**, and **switch** between them, and how they relate to **compute** in Snowflake.

---

## 🏗️ **What is a Virtual Warehouse?**

### ✅ Definition:

A **virtual warehouse** is a **cluster of compute resources** in Snowflake used to **process queries and data operations**.

### ✅ Key Point:

- **Virtual warehouses = Compute**
- **Storage = Where data lives**
- **Compute = Where queries run**

🧠 **Think of it like this**:

> If Snowflake is a kitchen:

- **Storage** is your fridge and pantry (where ingredients are kept).
- **Virtual warehouse** is your stove and oven (where cooking happens).

---

## ⚙️ **What Does `USE WAREHOUSE` Do?**

```sql
USE WAREHOUSE compute_wh;
```

- Tells Snowflake **which compute engine** to use for running your SQL queries.
- You can switch warehouses anytime depending on performance needs.

---

## 🛠️ **Creating a Virtual Warehouse**

### ✅ Option 1: Using Snowsight UI

1. Go to **Admin > Warehouses**
2. Click **+ Warehouse**
3. Name it (e.g., `warehouse_gilberto`)
4. Choose:
   - **Type**: Standard or Snowpark-optimized
   - **Size**: XS, S, M, L, etc.
5. Click **Create**

### ✅ Option 2: Using SQL

```sql
CREATE WAREHOUSE warehouse_dash;
```

- If you don’t specify size, it defaults to **X-Small**.

---

## 🔄 **Switching Between Warehouses**

### ✅ Using SQL:

```sql
USE WAREHOUSE warehouse_gilberto;
```

### ✅ Using UI:

- Click the **warehouse name** in the top-right of your worksheet and select a different one.

---

## 📋 **Listing All Warehouses**

```sql
SHOW WAREHOUSES;
```

- Displays all warehouses you’ve created, including their size and status.

---

## 💡 **Real Example: Calculating Profit**

Let’s say you want to calculate the profit for **Mango Sticky Rice** sold by the **Freezing Point** brand:

```sql
SELECT
  SALES_PRICE - COST_OF_GOODS_SOLD AS PROFIT
FROM tasty_bytes_sample_data.raw_pos.menu
WHERE TRUCK_BRAND_NAME = 'Freezing Point'
  AND ITEM_NAME = 'Mango Sticky Rice';
```

🧠 **Result**:

> Profit = \$3.75 per unit

---

## ✅ **Quick Recap Table**

| Concept            | Explanation                          | SQL Example                               |
| ------------------ | ------------------------------------ | ----------------------------------------- |
| Virtual Warehouse  | Compute engine                       | `CREATE WAREHOUSE my_wh;`                 |
| Use Warehouse      | Set active compute                   | `USE WAREHOUSE my_wh;`                    |
| Show Warehouses    | List all                             | `SHOW WAREHOUSES;`                        |
| Compute vs Storage | Compute = processing, Storage = data | —                                         |
| Profit Calculation | Sales - Cost                         | `SELECT SALES_PRICE - COST_OF_GOODS_SOLD` |

---

## 🧪 Practice Tip:

Try creating your own warehouse and run queries like:

- Count items per brand
- Average profit per menu type
- Compare performance between XS and S warehouses

Would you like a **step-by-step worksheet**, **SQL exercises**, or a **diagram** showing how compute and storage interact in Snowflake?

Here’s a **detailed and easy-to-understand summary** of the **“Virtual Warehouses Scaling: Part 1”** section from the Snowflake course, with **real-world examples** and simplified explanations to help you revise and explain the concept effectively.

---

## 🧠 **Virtual Warehouse Scaling – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand **vertical scaling** of virtual warehouses in Snowflake — how to **increase or decrease compute power** based on workload needs.

---

## ⚙️ **What is Vertical Scaling?**

### ✅ Definition:

**Vertical scaling** means changing the **size** of a virtual warehouse to increase or decrease the **compute resources** (CPU, memory, etc.).

🧠 **Think of it like this**:

> You’re resizing your machine depending on the job:

- Small job → Small machine
- Big job → Big machine

---

## 📊 **Why Scaling Matters?**

- **Efficiency**: Don’t waste big machines on small tasks.
- **Speed**: Don’t run big tasks on tiny machines.
- **Cost Control**: Use just enough compute to get the job done.

### 🧠 Example:

- Querying `menu` table (100 rows) → Small warehouse
- Querying `orders` table (600 million rows) → Medium or Large warehouse

---

## 🧮 **Warehouse Sizes and Credits**

| Size    | Compute Power | Credits/Hour | Formula |
| ------- | ------------- | ------------ | ------- |
| X-Small | 1 unit        | 1 credit     | $$2^0$$ |
| Small   | 2 units       | 2 credits    | $$2^1$$ |
| Medium  | 4 units       | 4 credits    | $$2^2$$ |
| Large   | 8 units       | 8 credits    | $$2^3$$ |
| ...     | ...           | ...          | ...     |
| 6XL     | 512 units     | 512 credits  | $$2^9$$ |

🧠 **Tip**: Sometimes using a **larger warehouse for a short time** is cheaper than using a **small one for a long time**.

---

## 🛠️ **How to Scale a Warehouse**

### ✅ Option 1: Using Snowsight UI

1. Go to **Admin > Warehouses**
2. Click **⋮ (three dots)** next to the warehouse
3. Click **Edit**
4. Choose new **size** from dropdown

### ✅ Option 2: Using SQL

```sql
ALTER WAREHOUSE warehouse_dash SET WAREHOUSE_SIZE = 'MEDIUM';
-- Run your query
ALTER WAREHOUSE warehouse_dash SET WAREHOUSE_SIZE = 'XSMALL';
```

---

## 💰 **Real Example: Profit Calculation**

Let’s say you want to calculate profit for **Tonkatsu Ramen**:

```sql
SELECT
  SALES_PRICE - COST_OF_GOODS_SOLD AS PROFIT
FROM tasty_bytes_sample_data.raw_pos.menu
WHERE ITEM_NAME = 'Tonkatsu Ramen';
```

🧠 **Result**:

> Profit = \$10+ per unit

You scaled up to **Medium** to run this query, then scaled back down to **X-Small** to save resources.

---

## ✅ **Quick Recap Table**

| Concept          | Explanation       | SQL Example                               |
| ---------------- | ----------------- | ----------------------------------------- |
| Vertical Scaling | Resize warehouse  | `ALTER WAREHOUSE ... SET SIZE = 'MEDIUM'` |
| Credits          | Cost per hour     | 1 credit for XS, 512 for 6XL              |
| Efficiency       | Match size to job | Small for menu, Medium for orders         |
| UI Scaling       | Manual resize     | Admin > Warehouses > Edit                 |
| SQL Scaling      | Code-based resize | `ALTER WAREHOUSE ...`                     |

---

## 🧪 Practice Tip:

Try this:

- Create a warehouse
- Scale it to Medium
- Run a query on a large table
- Scale it back to X-Small

Would you like a **step-by-step worksheet**, **SQL practice file**, or a **visual diagram** showing warehouse sizes and scaling logic?

Here’s a **detailed and easy-to-understand summary** of **“Virtual Warehouses Scaling: Part 2”** from the Snowflake course, with examples and simplified explanations to help you revise and explain the concept clearly.

---

## 🧠 **Virtual Warehouse Scaling – Part 2 Summary**

### 🎯 **Goal of This Section**:

To understand **horizontal scaling** in Snowflake — using **multiple clusters** to handle **concurrent queries** efficiently, and to learn about **auto resume**, **auto suspend**, and **manual suspension**.

---

## 🔄 **What is Horizontal Scaling?**

### ✅ Definition:

**Horizontal scaling** means adding **more clusters** to a virtual warehouse so it can handle **multiple queries at the same time**.

🧠 **Think of it like this**:

> If vertical scaling is upgrading your machine,  
> horizontal scaling is **adding more machines** to work in parallel.

---

## 👥 **Why Horizontal Scaling Matters?**

Imagine 3 data engineers are querying the same warehouse:

- Without horizontal scaling → Queries are **queued** one after another.
- With horizontal scaling → Queries are **processed simultaneously** using multiple clusters.

---

## 🛠️ **Creating a Multi-Cluster Warehouse**

### ✅ Using Snowsight UI:

1. Go to **Admin > Warehouses**
2. Click **+ Warehouse**
3. Name it (e.g., `warehouse_vino`)
4. Open **Advanced Options**
5. Toggle **Multi-cluster warehouse ON**
6. Set:
   - **Min clusters** = 1
   - **Max clusters** = 3

🧠 **Result**:

- Starts with 1 cluster
- Adds more clusters **only when needed** (up to 3)

---

### ✅ Using SQL:

```sql
CREATE WAREHOUSE warehouse_vino
WITH WAREHOUSE_SIZE = 'SMALL'
MAX_CLUSTER_COUNT = 4;
```

- Creates a **multi-cluster warehouse** with up to 4 clusters.

---

## 🔧 **Auto Resume & Auto Suspend**

### ✅ Auto Resume:

- **ON** by default
- Warehouse **automatically starts** when a query is submitted

### ✅ Auto Suspend:

- **ON** by default
- Warehouse **automatically stops** after inactivity (default: few minutes)

🧠 **Why it matters**:

- **Auto suspend saves credits**
- But **suspending too soon** clears cache → slower queries later

---

### ✅ Adjusting Settings via SQL:

```sql
ALTER WAREHOUSE warehouse_dash
SET AUTO_SUSPEND = 180,  -- 3 minutes
    AUTO_RESUME = FALSE;
```

- `AUTO_SUSPEND` is in **seconds**
- `AUTO_RESUME = FALSE` means manual start is required

---

## 🛑 **Manually Suspending a Warehouse**

### ✅ Using UI:

- Go to **Admin > Warehouses**
- Click **⋮ (three dots)** next to warehouse
- Click **Suspend**

### ✅ Using SQL:

```sql
ALTER WAREHOUSE warehouse_dash SUSPEND;
```

---

## ✅ **Quick Recap Table**

| Concept            | Explanation                  | SQL Example                   |
| ------------------ | ---------------------------- | ----------------------------- |
| Horizontal Scaling | Add clusters for concurrency | `MAX_CLUSTER_COUNT = 4`       |
| Auto Resume        | Auto-start on query          | `AUTO_RESUME = TRUE`          |
| Auto Suspend       | Auto-stop after idle         | `AUTO_SUSPEND = 180`          |
| Manual Suspend     | Stop warehouse manually      | `ALTER WAREHOUSE ... SUSPEND` |
| Multi-cluster      | Parallel query execution     | UI toggle or SQL create       |

---

## 🧪 Practice Tip:

Try this:

- Create a multi-cluster warehouse
- Run concurrent queries
- Adjust auto suspend/resume settings
- Manually suspend the warehouse

Would you like a **visual diagram**, **SQL cheat sheet**, or a **hands-on worksheet** to practice warehouse scaling scenarios?

Here’s a **detailed and easy-to-understand summary** of **“Stages and Basic Ingestion: Part 1”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Stages and Data Ingestion – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand what a **stage** is in Snowflake and how it helps in **loading data** into tables from external or internal sources.

---

## 📦 **What is a Stage in Snowflake?**

### ✅ Definition:

A **stage** is a **temporary storage area** used to **hold data before loading it into a table**.

🧠 **Think of it like this**:

> A stage is like a **waiting room** for your data before it enters the main building (your table).

---

## 🔄 **Why Use a Stage?**

- You **can’t directly load data** from your computer or cloud into a table.
- You first **upload it to a stage**, then **copy it into a table**.

---

## 🧑‍💻 **Types of Stages**

### ✅ 1. **External Stage**

- Data is stored in **external cloud storage** (e.g., AWS S3, Google Cloud, Azure).
- Snowflake **does not manage** this storage.
- You **don’t pay Snowflake** for storing this data.
- You **must provide a URL** and sometimes **credentials**.

#### 🧠 Example:

```sql
CREATE STAGE tasty_bytes_stage
URL='s3://snowflake-workshop-lab/tasty_bytes/'
FILE_FORMAT = (TYPE = 'CSV');
```

### ✅ 2. **Internal Stage**

- Data is stored **inside Snowflake-managed cloud storage**.
- Snowflake **handles security and billing**.
- **No external URL or credentials** needed.

#### 🧠 Example:

```sql
CREATE OR REPLACE STAGE internal_stage_test;
```

---

## 🛠️ **Steps in Data Ingestion**

1. **Set Role** (e.g., `ACCOUNTADMIN`)

   > Gives full access for setup (not best practice in real projects)

2. **Create Database and Schemas**

   - Example schemas: `raw`, `harmonized`, `analytics`

3. **Create Warehouses**
   - One for **loading data** (e.g., `demo_build_wh` – size: 3XL)
   - One for **analysis**

🧠 **Note**:

- A **3XL warehouse** is **64x more powerful** than XS
- Also **64x more expensive** (use briefly and drop)

4. **Create File Format**

   - Tells Snowflake how to read the file (CSV, JSON, etc.)

5. **Create Stage**
   - External stage pointing to S3 bucket

---

## ✅ **Quick Recap Table**

| Concept        | Explanation                          | SQL Example                       |
| -------------- | ------------------------------------ | --------------------------------- |
| Stage          | Temporary data holding area          | `CREATE STAGE ...`                |
| External Stage | Uses cloud storage outside Snowflake | `URL='s3://...'`                  |
| Internal Stage | Uses Snowflake-managed storage       | `CREATE STAGE internal_stage;`    |
| File Format    | Defines file type                    | `TYPE = 'CSV'`                    |
| Warehouse      | Compute engine for loading           | `CREATE WAREHOUSE demo_build_wh;` |

---

## 🧪 Practice Tip:

Try this:

- Create an internal stage
- Upload a sample CSV file
- Use `COPY INTO` to load data into a table

Would you like a **step-by-step worksheet**, **SQL practice file**, or a **diagram** showing the ingestion flow from stage to table?

Here’s a **detailed and easy-to-understand summary** of **“Stages and Basic Ingestion: Part 2”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Stages and Basic Ingestion – Part 2 Summary**

### 🎯 **Goal of This Section**:

To understand the **three types of internal stages**, how to **view staged files**, and how to **load data from a stage into a table** using the `COPY INTO` command.

---

## 📦 **Types of Internal Stages in Snowflake**

There are **three types** of internal stages:

| Type            | Description                                                   | Symbol        |
| --------------- | ------------------------------------------------------------- | ------------- |
| **User Stage**  | Each user has one. Can load data into multiple tables.        | `@~`          |
| **Table Stage** | Tied to a specific table. Can only load data into that table. | `@%`          |
| **Named Stage** | Custom stage. Can be used by multiple users and tables.       | `@stage_name` |

🧠 **Tip**:

> You’ll mostly use **named stages** because they’re flexible and reusable.

---

## 📂 **Uploading Data to Internal Stage**

- You use the `PUT` command to upload files from your **local machine** to an **internal stage**.
- This step is **not shown in this video**, but it’s essential when working with internal stages.

---

## 📋 **Viewing Files in a Stage**

To list files in a stage:

```sql
LIST @frostbyte_tasty_bytes.public.s3load;
```

- `LIST` shows all files in the stage.
- The `@` symbol is used to reference stages.

---

## 🧑‍🍳 **Preparing for Data Ingestion**

1. **Create Empty Tables**

   - Tables like `country`, `franchise`, `location`, `menu`, `truck`, `orders`, `customers`

2. **Create Views**
   - Views join and clean data across tables
   - Stored in `harmonized` and `analytics` schemas

🧠 **Note**:

> Views are like **virtual tables** created from SQL queries. You’ll learn more about them later.

---

## 🚀 **Loading Data Using COPY INTO**

Use the `COPY INTO` command to load data from a stage into a table:

```sql
COPY INTO country
FROM @frostbyte_tasty_bytes.public.s3load/country.csv
FILE_FORMAT = (TYPE = 'CSV');
```

- `COPY INTO` moves data from the stage to the table.
- You must ensure the **table structure matches** the file format.

---

## 🧪 **Observing Data Load History**

To check if files were loaded successfully:

```sql
SELECT file_name, error_count, status, last_load_time
FROM snowflake.account_usage.copy_history
ORDER BY last_load_time DESC
LIMIT 10;
```

- Shows recent file loads, errors, and status.
- Useful for **debugging** and **tracking ingestion**.

---

## ✅ **Quick Recap of Key Concepts**

| Step | What You Learned                                    |
| ---- | --------------------------------------------------- |
| 1️⃣   | What a stage is in Snowflake                        |
| 2️⃣   | How to create an external stage                     |
| 3️⃣   | Difference between external and internal stages     |
| 4️⃣   | Types of internal stages: user, table, named        |
| 5️⃣   | How to list files in a stage                        |
| 6️⃣   | How to load data using `COPY INTO`                  |
| 7️⃣   | How to check data load history using `copy_history` |

---

## 🧪 Practice Tip:

Try this:

- Create a named internal stage
- Upload a CSV file using `PUT`
- Create a matching table
- Use `COPY INTO` to load data
- Query `copy_history` to verify

Would you like a **hands-on worksheet**, **SQL practice file**, or a **diagram** showing the full ingestion flow from local file to Snowflake table?

Here’s a **detailed and easy-to-understand summary** of **“Databases and Schemas: Part I”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Databases and Schemas – Part I Summary**

### 🎯 **Goal of This Section**:

To understand what **databases** and **schemas** are in Snowflake, how they’re structured, and how to **navigate and query them** using the UI and SQL.

---

## 📦 **What Are Databases and Schemas?**

### ✅ **Database**:

A **container** for schemas and other database objects.

### ✅ **Schema**:

A **sub-container** inside a database that holds **tables**, **views**, **functions**, etc.

🧠 **Think of it like this**:

> - **Database** = Main folder
> - **Schema** = Sub-folder
> - **Tables/Views** = Files inside the sub-folder

---

## 🗂️ **Examples from the Course**

### ✅ Databases Seen:

1. **Snowflake Database** – Built-in, used for **observability** (e.g., `account_usage` schema)
2. **Snowflake Sample Data** – Trial account sample
3. **Tasty_Bytes Sample Data** – Created earlier in the course
4. **Frostbyte_Tasty_Bytes** – Created during ingestion

### ✅ Schemas Seen:

- `RAW_POS`, `RAW_CUSTOMER`, `HARMONIZED`, `ANALYTICS`

Each schema contains **tables** like `Menu`, `Order Detail`, `Order Header`, etc.

---

## 🔍 **How to Query a Table Using Full Path**

### ✅ Format:

```sql
SELECT *
FROM Frostbyte_Tasty_Bytes.RAW_POS.Menu;
```

- **Database**: `Frostbyte_Tasty_Bytes`
- **Schema**: `RAW_POS`
- **Table**: `Menu`

### ❌ If you skip the database:

```sql
SELECT * FROM RAW_POS.Menu;
```

You’ll get an error:

> “This session does not have a current database.”

🧠 **Tip**:  
Use `USE DATABASE` or `USE SCHEMA` to set context:

```sql
USE DATABASE Frostbyte_Tasty_Bytes;
USE SCHEMA RAW_POS;
```

---

## 📋 **Information Schema**

Each database has:

- **Public Schema** – Default schema
- **Information Schema** – Contains metadata views

### ✅ Example Query:

```sql
SELECT *
FROM Frostbyte_Tasty_Bytes.INFORMATION_SCHEMA.TABLES;
```

- Shows all tables in the database
- Useful for **metadata exploration**

---

## ✅ **Quick Recap Table**

| Concept     | Explanation           | SQL Example                                         |
| ----------- | --------------------- | --------------------------------------------------- |
| Database    | Main container        | `USE DATABASE Frostbyte_Tasty_Bytes;`               |
| Schema      | Sub-container         | `USE SCHEMA RAW_POS;`                               |
| Table       | Data object           | `SELECT * FROM RAW_POS.Menu;`                       |
| Full Path   | Database.Schema.Table | `SELECT * FROM Frostbyte_Tasty_Bytes.RAW_POS.Menu;` |
| Info Schema | Metadata access       | `SELECT * FROM INFORMATION_SCHEMA.TABLES;`          |

---

## 🧪 Practice Tip:

Try this:

- Explore databases in Snowsight UI
- Use `USE DATABASE` and `USE SCHEMA`
- Query a table using full path and short path
- Explore `INFORMATION_SCHEMA` to list tables

Would you like a **visual diagram**, **SQL cheat sheet**, or a **hands-on worksheet** to practice navigating databases and schemas in Snowflake?

Here’s a **detailed and easy-to-understand summary** of **“Databases and Schemas: Part 2”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Databases and Schemas – Part 2 Summary**

### 🎯 **Goal of This Section**:

To **practice creating, dropping, undropping, and using databases and schemas** in Snowflake using both the **UI** and **SQL commands**.

---

## 🏗️ **Working with Databases**

### ✅ 1. **Create a Database (UI)**

- Go to **Data > Databases**
- Click **+ Database**
- Name it (e.g., `test_database`)
- Click **Create**

🧠 Result:

- You’ll see two default schemas:
  - `PUBLIC`
  - `INFORMATION_SCHEMA`

---

### ✅ 2. **Drop a Database (UI)**

- Click the **three dots** next to the database name
- Select **Drop**

---

### ✅ 3. **Create a Database (SQL)**

```sql
CREATE DATABASE test_database;
```

### ✅ 4. **Show All Databases**

```sql
SHOW DATABASES;
```

- Lists all databases
- Shows type: `STANDARD`, `IMPORTED`, `APPLICATION`

---

### ✅ 5. **Drop a Database (SQL)**

```sql
DROP DATABASE test_database;
```

---

### ✅ 6. **Undrop a Database**

```sql
UNDROP DATABASE test_database;
```

🧠 Tip:

> Snowflake allows **undropping** recently dropped databases and schemas — a unique feature!

---

### ✅ 7. **Set Current Database**

```sql
USE DATABASE test_database;
```

- Sets context for future queries
- Updates the dropdown in Snowsight UI

---

## 📂 **Working with Schemas**

### ✅ 1. **Create a Schema (SQL)**

```sql
CREATE SCHEMA test_schema;
```

- If a database is already selected, schema is created inside it.

---

### ✅ 2. **Show Schemas**

```sql
SHOW SCHEMAS;
```

- Lists all schemas in the current database

---

### ✅ 3. **Describe Database**

```sql
DESCRIBE DATABASE test_database;
```

- Gives basic info (less detailed than `SHOW SCHEMAS`)

---

### ✅ 4. **Drop a Schema**

```sql
DROP SCHEMA test_schema;
```

---

### ✅ 5. **Undrop a Schema**

```sql
UNDROP SCHEMA test_schema;
```

---

## 🔁 **Consistent Syntax Across Objects**

Snowflake uses **similar commands** for:

- **Databases**
- **Schemas**
- **Tables**

### ✅ Common Commands:

- `CREATE`
- `DROP`
- `UNDROP`
- `SHOW`
- `USE`
- `ALTER` (not covered yet)

🧠 Tip:

> This consistency makes Snowflake **easy to learn and use**.

---

## ✅ **Quick Recap Table**

| Action | Database Example           | Schema Example               |
| ------ | -------------------------- | ---------------------------- |
| Create | `CREATE DATABASE test_db;` | `CREATE SCHEMA test_schema;` |
| Drop   | `DROP DATABASE test_db;`   | `DROP SCHEMA test_schema;`   |
| Undrop | `UNDROP DATABASE test_db;` | `UNDROP SCHEMA test_schema;` |
| Show   | `SHOW DATABASES;`          | `SHOW SCHEMAS;`              |
| Use    | `USE DATABASE test_db;`    | `USE SCHEMA test_schema;`    |

---

## 🧪 Practice Tip:

Try this:

- Create a new database and schema
- Drop and undrop both
- Use `SHOW` and `DESCRIBE` to explore metadata

Would you like a **hands-on worksheet**, **SQL practice file**, or a **diagram** showing the hierarchy of databases, schemas, and tables in Snowflake?

Here’s a **detailed and easy-to-understand summary** of **“Tables: Part 1”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Tables in Snowflake – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand how to **create a table**, learn about **data types**, and explore how Snowflake organizes data internally.

---

## 📋 **What is a Table in Snowflake?**

- A **table** stores data in **rows and columns**, just like in Excel or Pandas.
- Under the hood, Snowflake stores data in **micro-partitions** (advanced topic, not covered here).

🧠 **Think of it like this**:

> A table is like a spreadsheet, but optimized for big data and fast querying.

---

## 🛠️ **Creating a Table**

### ✅ Option 1: Using the UI

1. Go to **Data > Databases > TEST_DATABASE > TEST_SCHEMA**
2. Click **Create > Table > Standard**
3. You’ll be taken to a **template editor** where you must define:
   - **Table name**
   - **Column names**
   - **Data types**

### ✅ Option 2: Using SQL

```sql
CREATE TABLE test_table (
  id NUMBER,
  name VARCHAR,
  is_active BOOLEAN,
  created_on DATE,
  metadata VARIANT,
  location GEOGRAPHY
);
```

---

## 🔢 **Snowflake Data Types**

There are **6 categories** of data types:

| Category            | Examples                     | Notes                                 |
| ------------------- | ---------------------------- | ------------------------------------- |
| **Numeric**         | `NUMBER`, `INT`, `FLOAT`     | Many aliases resolve to same type     |
| **String & Binary** | `VARCHAR`, `STRING`, `TEXT`  | All mean the same thing               |
| **Logical**         | `BOOLEAN`                    | True/False values                     |
| **Date & Time**     | `DATE`, `TIMESTAMP`          | For time-based data                   |
| **Semi-Structured** | `VARIANT`, `OBJECT`, `ARRAY` | For JSON/XML-like data                |
| **Geospatial**      | `GEOGRAPHY`                  | For location data (maps, coordinates) |

🧠 **Tip**:

> You don’t need to memorize all types. Many are interchangeable. Snowflake supports aliases to make migration from other SQL systems easier.

---

## 📏 **Precision and Size Defaults**

- `NUMBER` defaults to **precision 38** and **scale 0**
- `VARCHAR` defaults to **max 16 MB** (16,777,216 bytes)

🧠 **Note**:

> Snowflake only uses the space needed, so specifying smaller sizes doesn’t improve performance—except in some BI tools.

---

## 🔍 **Querying the Table**

After creating the table, you can query it:

```sql
SELECT *
FROM TEST_DATABASE.TEST_SCHEMA.TEST_TABLE;
```

- You’ll see **column names**, but **no data** (because it’s a new empty table).

---

## ✅ **Quick Recap Table**

| Concept      | Explanation                 | SQL Example                          |
| ------------ | --------------------------- | ------------------------------------ |
| Table        | Stores data in rows/columns | `CREATE TABLE test_table (...)`      |
| Data Types   | Define column format        | `VARCHAR`, `NUMBER`, `BOOLEAN`, etc. |
| UI Creation  | Visual editor               | Data > Create Table                  |
| SQL Creation | Code-based                  | `CREATE TABLE ...`                   |
| Query Table  | View contents               | `SELECT * FROM ...`                  |

---

## 🧪 Practice Tip:

Try this:

- Create a table with one column from each data type category
- Query the table
- Insert sample data (coming in next video)

Would you like a **hands-on worksheet**, **SQL practice file**, or a **cheat sheet** of Snowflake data types with examples?

Here’s a **detailed and easy-to-understand summary** of **“Tables: Part 2”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Tables in Snowflake – Part 2 Summary**

### 🎯 **Goal of This Section**:

To learn how to **insert data into a table**, and how to **drop**, **undrop**, and **inspect metadata** for tables in Snowflake.

---

## 📥 **Inserting Data into a Table**

### ✅ Example:

```sql
INSERT INTO TEST_DATABASE.TEST_SCHEMA.TEST_TABLE
VALUES (1, 'Sample Name', TRUE, '2025-09-05', NULL, NULL);
```

- Inserts one row into the table.
- `NULL` is used for `VARIANT` and `GEOGRAPHY` types (more complex to populate).
- After inserting, you can query the table:

```sql
SELECT * FROM TEST_DATABASE.TEST_SCHEMA.TEST_TABLE;
```

🧠 **Result**:

> You’ll see the row you just inserted.

---

## 🗑️ **Dropping and Undropping a Table**

### ✅ Drop Table:

```sql
DROP TABLE TEST_DATABASE.TEST_SCHEMA.TEST_TABLE;
```

- Deletes the table (but can be recovered).

### ✅ Show Tables in Schema:

```sql
SHOW TABLES IN TEST_DATABASE.TEST_SCHEMA;
```

- Shows all tables in the specified schema.

### ✅ Undrop Table:

```sql
UNDROP TABLE TEST_DATABASE.TEST_SCHEMA.TEST_TABLE;
```

- Recovers the dropped table.

🧠 **Fun Analogy**:

> Like saying “Drop dead!” and then “Wait! Undrop!” 😄

---

## 📊 **Viewing Table Metadata**

### ✅ Show All Tables:

```sql
SHOW TABLES;
```

- Lists all tables across all databases and schemas.
- Includes metadata like:
  - Number of rows
  - Storage size (bytes)

### ✅ View Storage Metrics:

```sql
SELECT *
FROM SNOWFLAKE.ACCOUNT_USAGE.TABLE_STORAGE_METRICS;
```

- Shows detailed storage info for manually created tables.
- Useful for **observability and optimization**.

---

## 🔍 **Revisiting the `ORDER_DETAIL` Table**

- Created earlier with:

```sql
CREATE OR REPLACE TABLE FROSTBYTE_TASTY_BYTES.RAW_POS.ORDER_DETAIL (
  ORDER_ID NUMBER(38, 0),
  ITEM_ID NUMBER(38, 0),
  QUANTITY NUMBER(5, 0),
  UNIT_PRICE NUMBER(38, 4),
  ...
);
```

- **9 columns**: 7 `NUMBER`, 2 `VARCHAR`
- **670+ million rows** – a **massive table**!

🧠 **Precision & Scale**:

- `NUMBER(5, 0)` → Up to 5 digits, no decimals
- `NUMBER(38, 4)` → Up to 38 digits, 4 after decimal

---

## ✅ **Quick Recap Table**

| Action          | SQL Example                           | Notes            |
| --------------- | ------------------------------------- | ---------------- |
| Insert Data     | `INSERT INTO ... VALUES (...)`        | Adds a row       |
| Drop Table      | `DROP TABLE ...`                      | Deletes table    |
| Undrop Table    | `UNDROP TABLE ...`                    | Recovers table   |
| Show Tables     | `SHOW TABLES IN ...`                  | Lists tables     |
| Storage Metrics | `SELECT * FROM TABLE_STORAGE_METRICS` | Shows size, rows |

---

## 🧪 Practice Tip:

Try this:

- Insert multiple rows into a table
- Drop and undrop the table
- Use `SHOW TABLES` and `TABLE_STORAGE_METRICS` to inspect metadata

Would you like a **hands-on worksheet**, **SQL practice file**, or a **diagram** showing table lifecycle and metadata flow in Snowflake?

Here’s a **detailed and easy-to-understand summary** of **“Views: Part 1”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Views in Snowflake – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand what **views** are, how to **create**, **query**, and **manage** them, and the difference between **standard views** and **materialized views**.

---

## 👓 **What is a View?**

### ✅ Definition:

A **view** is a **saved SQL query** that behaves like a virtual table.

🧠 **Think of it like this**:

> A view is like a **live report** that runs a query every time you open it.  
> It doesn’t store data—it just shows results based on the latest data.

---

## 🧩 **Types of Views**

| Type                  | Description                        | Key Difference                                   |
| --------------------- | ---------------------------------- | ------------------------------------------------ |
| **Standard View**     | Saves the query                    | Runs the query every time                        |
| **Materialized View** | Saves the query **and** the result | Faster, but uses more resources and auto-updates |

🧠 **Note**:

> You **can’t use JOINs** in materialized views.

---

## 🛠️ **Creating a View**

### ✅ Example:

```sql
CREATE VIEW frostbyte_tasty_bytes.harmonized.orders_v AS
SELECT ...
FROM ...
JOIN ...
WHERE ...;
```

- This creates a view called `orders_v` in the `harmonized` schema.
- You can query it like a table:

```sql
SELECT COUNT(*) FROM frostbyte_tasty_bytes.harmonized.orders_v;
```

---

## 📋 **View Commands in Snowflake**

| Command         | Purpose                        | Example                             |
| --------------- | ------------------------------ | ----------------------------------- |
| `CREATE VIEW`   | Create a view                  | `CREATE VIEW my_view AS SELECT ...` |
| `DROP VIEW`     | Delete a view                  | `DROP VIEW my_view;`                |
| `SHOW VIEWS`    | List all views                 | `SHOW VIEWS;`                       |
| `DESCRIBE VIEW` | View metadata                  | `DESCRIBE VIEW my_view;`            |
| `ALTER VIEW`    | Modify view (not covered here) | —                                   |

🧠 **Important**:

> Unlike tables, **you can’t undrop a view**. If you drop it, you’ll need to recreate it.

---

## 🧪 **Practice Example**

### ✅ Create a Simple View:

```sql
CREATE VIEW frostbyte_tasty_bytes.harmonized.brand_names AS
SELECT truck_brand_name
FROM frostbyte_tasty_bytes.raw_pos.menu;
```

### ✅ Show Views:

```sql
SHOW VIEWS;
```

### ✅ Drop View:

```sql
DROP VIEW frostbyte_tasty_bytes.harmonized.brand_names;
```

### ✅ Describe View:

```sql
DESCRIBE VIEW frostbyte_tasty_bytes.harmonized.orders_v;
```

---

## ✅ **Quick Recap Table**

| Concept           | Explanation                                   |
| ----------------- | --------------------------------------------- |
| View              | Saved SQL query                               |
| Standard View     | Runs query each time                          |
| Materialized View | Stores query result                           |
| Commands          | `CREATE`, `DROP`, `SHOW`, `DESCRIBE`, `ALTER` |
| No Undrop         | Views can’t be recovered once dropped         |

---

## 🧪 Practice Tip:

Try this:

- Create a view with a `SELECT` and `WHERE` clause
- Query the view
- Drop and recreate it
- Use `SHOW VIEWS` and `DESCRIBE VIEW` to explore metadata

Would you like a **hands-on worksheet**, **SQL practice file**, or a **comparison chart** between views and materialized views with use cases?

Here’s a **detailed and easy-to-understand summary** of **“Views: Part 2”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Views in Snowflake – Part 2 Summary**

### 🎯 **Goal of This Section**:

To understand **materialized views**, how they differ from standard views, and why you might use them.

---

## 🧩 **Materialized Views vs. Standard Views**

| Feature          | **Standard View**             | **Materialized View**            |
| ---------------- | ----------------------------- | -------------------------------- |
| Stores Query     | ✅ Yes                        | ✅ Yes                           |
| Stores Results   | ❌ No                         | ✅ Yes                           |
| Auto Refresh     | ❌ No                         | ✅ Yes (when base table updates) |
| Performance      | Slower (runs query each time) | Faster (reads stored result)     |
| Joins Allowed    | ✅ Yes                        | ❌ No (only one table allowed)   |
| Can Be Dropped   | ✅ Yes                        | ✅ Yes                           |
| Can Be Undropped | ❌ No                         | ❌ No                            |

---

## 🛠️ **Creating a Materialized View**

### ✅ Example:

```sql
CREATE MATERIALIZED VIEW frostbyte_tasty_bytes.harmonized.brand_names_materialized AS
SELECT DISTINCT truck_brand_name
FROM frostbyte_tasty_bytes.raw_pos.menu;
```

- Saves the **result** of the query, not just the query itself.
- Useful for **frequently accessed** data.

---

## 🔍 **Querying and Managing Materialized Views**

### ✅ Query the View:

```sql
SELECT * FROM frostbyte_tasty_bytes.harmonized.brand_names_materialized;
```

### ✅ Show All Views:

```sql
SHOW VIEWS;
```

- Includes both standard and materialized views.
- Column `is_materialized` = `TRUE` for materialized views.

### ✅ Show Only Materialized Views:

```sql
SHOW MATERIALIZED VIEWS;
```

- Includes `refreshed_on` column to show last update time.

### ✅ Describe View:

```sql
DESCRIBE VIEW frostbyte_tasty_bytes.harmonized.brand_names_materialized;
```

- Same output as for standard views.

### ✅ Drop Materialized View:

```sql
DROP MATERIALIZED VIEW frostbyte_tasty_bytes.harmonized.brand_names_materialized;
```

🧠 **Note**:

> You **must use `DROP MATERIALIZED VIEW`**, not just `DROP VIEW`.

---

## 💡 **Why Use Views or Materialized Views?**

### ✅ 1. **Cleaner Code**

- Save complex queries as views to avoid repetition and reduce errors.

### ✅ 2. **Access Control**

- Give users access to **specific columns or rows** via views, without exposing full tables.

### ✅ 3. **Performance**

- Materialized views are **faster** for repeated queries.
- They **auto-refresh** when base data changes.

---

## 🧠 **Bonus: Dynamic Tables**

- Mentioned briefly as a **more flexible alternative** to materialized views.
- Can be refreshed on a **custom schedule**.
- Not covered in this video, but useful to know they exist.

---

## ✅ **Quick Recap Table**

| Action                       | Command                                      |
| ---------------------------- | -------------------------------------------- |
| Create Materialized View     | `CREATE MATERIALIZED VIEW ... AS SELECT ...` |
| Query View                   | `SELECT * FROM ...`                          |
| Show Views                   | `SHOW VIEWS;`                                |
| Show Only Materialized Views | `SHOW MATERIALIZED VIEWS;`                   |
| Describe View                | `DESCRIBE VIEW ...`                          |
| Drop Materialized View       | `DROP MATERIALIZED VIEW ...`                 |

---

## 🧪 Practice Tip:

Try this:

- Create a materialized view on a single table
- Query it and check `refreshed_on`
- Drop it and recreate it as a standard view
- Compare performance and flexibility

Would you like a **comparison chart**, **SQL worksheet**, or a **diagram** showing how views, materialized views, and dynamic tables relate to each other?

Here’s a **detailed and easy-to-understand summary** of **“Semistructured Data Types”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Semistructured Data in Snowflake – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand what **semistructured data** is, how Snowflake handles it, and how to work with its **three key data types**: `VARIANT`, `OBJECT`, and `ARRAY`.

---

## 📦 **What is Semistructured Data?**

### ✅ Definition:

Semistructured data is **not flat like a table**, but it **has structure**—often in **hierarchical** or **nested** formats.

🧠 **Think of it like this**:

> - **Structured data**: Tables (rows & columns)
> - **Unstructured data**: Images, raw text
> - **Semistructured data**: JSON, XML, Parquet, Avro, ORC

### ✅ Common Use Cases:

- Sensor data
- Web logs
- API responses
- Health metrics
- Product catalogs

---

## 🔍 **Example from Tasty Bytes Dataset**

```sql
SELECT menu_item_name, menu_item_health_metrics_obj
FROM frostbyte_tasty_bytes.raw_pos.menu;
```

- `menu_item_health_metrics_obj` contains **JSON** with:
  - Ingredients
  - Health flags (e.g., dairy-free)
  - Nutrition info

---

## 🧩 **Snowflake Data Types for Semistructured Data**

### ✅ 1. **VARIANT**

- **Most flexible** type
- Can hold **any data type** (number, string, object, array, etc.)
- Snowflake **remembers the original type**

#### 🧠 Example:

```sql
CREATE TABLE test_menu AS
SELECT cost_of_goods_usd AS cost_of_goods_variant
FROM frostbyte_tasty_bytes.raw_pos.menu;
```

- Column `cost_of_goods_variant` is of type `VARIANT`
- You can check its internal type:

```sql
SELECT TYPEOF(cost_of_goods_variant)
FROM test_menu;
```

- You can even do math:

```sql
SELECT cost_of_goods_variant, cost_of_goods_variant * 2.0
FROM test_menu;
```

---

### ✅ 2. **OBJECT**

- Like a **dictionary** in Python
- Stores **key-value pairs**
- Keys are strings, values are `VARIANT`

#### 🧠 Example:

```sql
SELECT menu_item_health_metrics_obj['menu_item_id']
FROM frostbyte_tasty_bytes.raw_pos.menu;
```

- Extracts the value for key `menu_item_id` from the JSON object

---

### ✅ 3. **ARRAY**

- Like a **list** in Python
- Ordered collection of items
- Each item is of type `VARIANT`

#### 🧠 Example:

```sql
SELECT ingredients_array[0], ingredients_array[1]
FROM some_table;
```

- Accesses first and second items in the array

---

## ✅ **Quick Recap Table**

| Data Type | Description                       | Access Method            |
| --------- | --------------------------------- | ------------------------ |
| `VARIANT` | Flexible container for any type   | `TYPEOF(column)`         |
| `OBJECT`  | Key-value pairs (like dictionary) | `column['key']`          |
| `ARRAY`   | Ordered list of values            | `column[0]`, `column[1]` |

---

## 🧪 Practice Tip:

Try this:

- Query a `VARIANT` column and check its type
- Extract a value from an `OBJECT` using a key
- Access elements from an `ARRAY` using index

Would you like a **hands-on worksheet**, **SQL practice file**, or a **diagram** showing how to navigate nested JSON structures in Snowflake?

Here’s a **detailed and easy-to-understand summary** of **“Semistructured Data Manipulation”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Semistructured Data Manipulation – Summary**

### 🎯 **Goal of This Section**:

To learn how to **extract and manipulate data** from **JSON columns** in Snowflake using:

- **Dot and bracket notation**
- **LATERAL FLATTEN**
- **Variant, Object, and Array types**

---

## 📦 **Recap of Semistructured Data Types**

| Type      | Description                       | Access Method            |
| --------- | --------------------------------- | ------------------------ |
| `VARIANT` | Flexible container for any type   | `TYPEOF(column)`         |
| `OBJECT`  | Key-value pairs (like dictionary) | `column['key']`          |
| `ARRAY`   | Ordered list of values            | `column[0]`, `column[1]` |

---

## 🔍 **Accessing JSON Data – Two Methods**

### ✅ 1. **Dot & Bracket Notation**

#### 🧪 Example: Extracting First Ingredient

To extract the first ingredient from a deeply nested JSON column:

```sql
SELECT
  MENU_ITEM_HEALTH_METRICS_OBJ'menu_item_health_metrics''ingredients'
FROM frostbyte_tasty_bytes.raw_pos.menu;
```

- Each layer digs deeper into the JSON structure:
  - `['menu_item_health_metrics']` → array of health metrics
  - `(0)` → first element
  - `['ingredients']` → key inside that object
  - `(0)` → first ingredient

---

### ✅ 2. **Using `LATERAL FLATTEN`**

#### 🧪 Example:

```sql
SELECT
  value'ingredients' AS first_ingredient
FROM frostbyte_tasty_bytes.raw_pos.menu,
LATERAL FLATTEN(input => menu_item_health_metrics_obj['menu_item_health_metrics']);
```

- `LATERAL FLATTEN` expands arrays into rows.
- `value` is a special column created by `FLATTEN`.
- You can then extract nested values from `value`.

🧠 **Tip**:

> This method is **cleaner and more scalable** when working with arrays.

---

## 📊 **Creating a View for Analytics**

### ✅ Goal:

Count menu items that are:

- Healthy
- Gluten-free
- Dairy-free
- Nut-free

### ✅ View Creation:

```sql
CREATE OR REPLACE VIEW frostbyte_tasty_bytes.analytics.menu_v AS
SELECT
  value['is_healthy_flag']::STRING AS healthy_flag,
  value['is_gluten_free_flag']::STRING AS gluten_free_flag,
  value['is_dairy_free_flag']::STRING AS dairy_free_flag,
  value['is_nut_free_flag']::STRING AS nut_free_flag
FROM frostbyte_tasty_bytes.raw_pos.menu,
LATERAL FLATTEN(input => menu_item_health_metrics_obj['menu_item_health_metrics']);
```

### ✅ Aggregation Query:

```sql
SELECT
  COUNT(DISTINCT menu_item_id) AS total_items,
  SUM(CASE WHEN healthy_flag = 'Y' THEN 1 ELSE 0 END) AS healthy_count,
  SUM(CASE WHEN gluten_free_flag = 'Y' THEN 1 ELSE 0 END) AS gluten_free_count,
  SUM(CASE WHEN dairy_free_flag = 'Y' THEN 1 ELSE 0 END) AS dairy_free_count,
  SUM(CASE WHEN nut_free_flag = 'Y' THEN 1 ELSE 0 END) AS nut_free_count
FROM frostbyte_tasty_bytes.analytics.menu_v;
```

🧠 **Result**:

- 95 nut-free items
- 81 dairy-free items
- 23 healthy items

---

## ✅ **Quick Recap Table**

| Task                 | Method               | Example                            |
| -------------------- | -------------------- | ---------------------------------- |
| Access JSON key      | Bracket notation     | `column['key']`                    |
| Access array element | Index                | `column[0]`                        |
| Flatten array        | `LATERAL FLATTEN`    | `FROM table, LATERAL FLATTEN(...)` |
| Create view          | `CREATE VIEW`        | Save query for reuse               |
| Aggregate flags      | `SUM(CASE WHEN ...)` | Count specific conditions          |

---

## 🧪 Practice Tip:

Try this:

- Use `LATERAL FLATTEN` to extract nested JSON values
- Create a view with health flags
- Run aggregation queries on the view

Would you like a **hands-on worksheet**, **SQL practice file**, or a **diagram** showing how to traverse nested JSON structures step-by-step?

Here’s a **detailed and easy-to-understand summary** of the **“Snowflake Architecture Overview”** from the course, with practical explanations to help you revise and explain the concept confidently.

---

## 🧠 **Snowflake Architecture – Summary**

### 🎯 **Goal of This Section**:

To understand the **four-layer architecture** of Snowflake and how each layer contributes to scalability, flexibility, and performance.

---

## 🏗️ **Snowflake’s Four-Layer Architecture**

| Layer                                | Description                 | Key Features                                                          |
| ------------------------------------ | --------------------------- | --------------------------------------------------------------------- |
| **1. Optimized Storage**             | Where data is stored        | Structured, semi-structured (JSON, XML), unstructured (PDF, images)   |
| **2. Elastic Multi-Cluster Compute** | Where queries are processed | Scalable compute, multiple clusters, supports SQL, Python, Java       |
| **3. Cloud Services**                | Manages operations          | Auto-upgrades, caching, Time Travel, zero-copy cloning                |
| **4. Snowgrid**                      | Enables global data sharing | Cross-region/cloud replication, business continuity, app distribution |

---

### ✅ **1. Optimized Storage**

- Stores **all types of data**: structured, semi-structured, unstructured
- Built on **Blob Storage** (e.g., AWS S3, Azure Blob)
- Snowflake handles:
  - **Micro-partitioning**
  - **Compression**
  - **Encryption**
- No need to migrate data as it grows
- Supports **open formats** like Apache Iceberg

🧠 **Think of it like**:

> A smart warehouse that organizes and secures your data automatically.

---

### ✅ **2. Elastic Multi-Cluster Compute**

- **Separates compute from storage** (a major innovation)
- Also **separates compute from compute**:
  - Multiple clusters can query the same data **without conflict**
- Supports **multiple languages**:
  - SQL, Python, Java (via Snowpark)
- Enables **scalable performance** for concurrent users

🧠 **Think of it like**:

> A fleet of kitchens that can cook from the same pantry without bumping into each other.

---

### ✅ **3. Cloud Services Layer**

- Handles **platform operations**:
  - Automatic upgrades (no downtime)
  - Query result caching
  - Metadata management
  - Time Travel (recover past data)
  - Zero-copy cloning (duplicate data instantly)
- Ensures **high concurrency** and **smooth performance**

🧠 **Think of it like**:

> The control room that keeps everything running smoothly behind the scenes.

---

### ✅ **4. Snowgrid**

- Enables **cross-region and cross-cloud** data sharing
- Works across:
  - AWS
  - Azure
  - Google Cloud
- Supports:
  - **Replication**
  - **Failover**
  - **App distribution**
  - **Business continuity**

🧠 **Think of it like**:

> A global highway system that connects data and apps across clouds and continents.

---

## ✅ **Quick Recap Table**

| Layer          | Role              | Benefits                                   |
| -------------- | ----------------- | ------------------------------------------ |
| Storage        | Holds data        | Secure, scalable, flexible                 |
| Compute        | Processes queries | Fast, concurrent, language-flexible        |
| Cloud Services | Manages platform  | Auto-updates, caching, Time Travel         |
| Snowgrid       | Connects globally | Cross-cloud sharing, replication, failover |

---

## 🧪 Practice Tip:

Try this:

- Match Snowflake features (e.g., Time Travel, Snowpark, zero-copy cloning) to their architectural layer
- Explain to a peer how Snowflake separates storage and compute—and why that matters

Would you like a **diagram**, **flashcards**, or a **quiz** to help reinforce Snowflake’s architecture?

Here’s a **clear and concise wrap-up** of everything you’ve learned so far about **Snowflake’s core objects and architecture**, designed to help you revise and explain the concepts confidently.

---

## ✅ **Snowflake Core Concepts Recap**

### 🧭 **1. Snowsight (UI)**

- Snowflake’s browser-based interface
- Lets you create and manage:
  - Worksheets
  - Warehouses
  - Databases, Schemas, Tables, Views

---

### ⚙️ **2. Virtual Warehouses**

- **Compute engines** that run queries
- Can be:
  - **Scaled vertically** (XS → XL → 6XL)
  - **Scaled horizontally** (multi-cluster for concurrency)
- Commands:
  ```sql
  USE WAREHOUSE my_wh;
  ALTER WAREHOUSE my_wh SET WAREHOUSE_SIZE = 'MEDIUM';
  ```

---

### 🗂️ **3. Databases, Schemas, Tables**

- **Database**: Main container
- **Schema**: Sub-container inside a database
- **Table**: Stores actual data (rows & columns)

🧠 **Hierarchy**:

> Database → Schema → Table

---

### 👓 **4. Views**

- **Standard View**: Saved query
- **Materialized View**: Saved query **+ saved result**
  - Auto-refreshes when base table updates
  - Faster but limited (no joins)

---

### 📦 **5. Semi-Structured Data**

- Formats: JSON, XML, Avro, ORC, Parquet
- Snowflake data types:
  - `VARIANT`: Flexible container
  - `OBJECT`: Key-value pairs
  - `ARRAY`: Ordered list

🧠 **Access Methods**:

```sql
-- Dot notation
SELECT column:key FROM table;

-- Bracket notation
SELECT column['key'] FROM table;

-- Flatten arrays
SELECT value['ingredients'][0]
FROM table, LATERAL FLATTEN(input => column['array_key']);
```

---

### 🏗️ **6. Snowflake Architecture**

| Layer                             | Role                                                  |
| --------------------------------- | ----------------------------------------------------- |
| **Optimized Storage**             | Stores structured, semi-structured, unstructured data |
| **Elastic Multi-Cluster Compute** | Runs queries, supports multiple languages             |
| **Cloud Services**                | Handles upgrades, caching, Time Travel, cloning       |
| **Snowgrid**                      | Enables cross-region/cloud sharing and replication    |

---

## 🎯 **You’ve Learned How To:**

- Navigate Snowsight and use worksheets
- Create and manage warehouses, databases, schemas, tables, views
- Work with semi-structured data using `VARIANT`, `OBJECT`, `ARRAY`
- Use `LATERAL FLATTEN` to extract nested JSON values
- Understand Snowflake’s architecture and scalability

---

Would you like a **printable cheat sheet**, **flashcards**, or a **mind map** to help you revise all these topics visually?

Here’s a **clear and easy-to-understand summary** of the **“Intro to Snowflake Feature Overview”** section from the course, designed to help you revise and explain the transition from Snowflake’s core objects to its powerful features.

---

## 🧠 **Snowflake Feature Overview – Summary**

### 🎯 **Goal of This Section**:

To introduce the **next phase** of the course, where you’ll learn how to **use** Snowflake’s core objects through **advanced features** like:

- **Time Travel**
- **Cloning**
- **Stored Procedures**
- **User-Defined Functions (UDFs)**
- **Snowpark DataFrames**
- And more...

---

## 🧱 **Course Structure Recap**

### ✅ **Part 1: Core Building Blocks**

You’ve already learned:

- How to use **Snowsight** (Snowflake’s UI)
- How to create and manage:
  - **Virtual Warehouses** (compute)
  - **Databases, Schemas, Tables**
  - **Views** (standard and materialized)
  - **Semi-structured data** (JSON, XML, etc.)
- Snowflake’s **four-layer architecture**:
  - **Storage**
  - **Compute**
  - **Cloud Services**
  - **Snowgrid**

---

### 🚀 **Part 2: Using the Building Blocks**

Now you’ll learn **how to use** those objects more powerfully through features like:

| Feature                           | What It Does                                      |
| --------------------------------- | ------------------------------------------------- |
| **Time Travel**                   | Recover deleted or changed data                   |
| **Cloning**                       | Instantly duplicate tables, schemas, or databases |
| **Stored Procedures**             | Automate tasks using SQL logic                    |
| **User-Defined Functions (UDFs)** | Create custom functions for reuse                 |
| **Snowpark**                      | Use Python, Java, or Scala for data engineering   |

🧠 **Think of it like this**:

> Part 1 gave you the **tools**.  
> Part 2 shows you how to **build cool stuff** with those tools.

---

## 🍽️ **Dataset Used: Tasty Bytes**

You’ll continue working with the **Tasty Bytes food truck dataset**, which includes:

- Menu items
- Ingredients
- Health metrics
- Orders and customers

🧠 **Fun Note**:

> Your work with this fictitious dataset helps fictitious people enjoy fictitious mango sticky rice. 😄

---

## ✅ **Quick Recap Table**

| Part   | Focus        | What You Learned                     |
| ------ | ------------ | ------------------------------------ |
| Part 1 | Core Objects | UI, Warehouses, Tables, Views, JSON  |
| Part 2 | Features     | Time Travel, Cloning, UDFs, Snowpark |

---

Would you like a **feature-by-feature cheat sheet**, a **comparison chart**, or a **hands-on worksheet** to help you practice these upcoming Snowflake features?

Here’s a **detailed and easy-to-understand summary** of **“Time Travel: Part 1”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Snowflake Time Travel – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand **what Time Travel is**, how it works through **data retention**, and how it helps recover past versions of data in Snowflake.

---

## ⏳ **What is Time Travel in Snowflake?**

### ✅ Definition:

**Time Travel** lets you **query, restore, or clone** data from a **previous point in time**—even if it was deleted or changed.

🧠 **Think of it like**:

> An “Undo” button for your database.

---

## 📦 **How It Works: Data Retention**

- Snowflake tracks changes to data for a **retention period**.
- Default retention for **permanent tables**: **1 day**
- On **Enterprise Edition**, you can extend it up to **90 days**

### ✅ Example:

```sql
ALTER TABLE frostbyte_tasty_bytes.raw_pos.test_menu
SET DATA_RETENTION_TIME_IN_DAYS = 90;
```

- This sets the retention window to 90 days.
- You can **query or recover** data from any point in that window.

---

## 🧑‍🔧 **Important Notes**

- **Retention time ≠ table lifetime**  
  → Tables persist indefinitely unless dropped.
- Retention time only affects **how far back you can go** using Time Travel.
- **Higher retention = more storage cost** (especially with high data churn)

---

## 🧪 **Time Travel Already Used in the Course**

You’ve already used Time Travel when you:

- **Undropped** a table, schema, or database
- Saw dropped tables listed in `SHOW TABLES` (within retention period)

---

## 🔍 **Coming Up Next**

You’ll learn **three ways** to use Time Travel:

1. **Querying a table as of a specific timestamp**
2. **Querying a table as of N seconds ago**
3. **Querying a table before a specific query was run**

---

## ✅ **Quick Recap Table**

| Feature          | Description                                | Example                              |
| ---------------- | ------------------------------------------ | ------------------------------------ |
| Time Travel      | Recover past data                          | `SELECT * FROM table AT (TIMESTAMP)` |
| Retention Period | Time window for recovery                   | Default: 1 day, Max: 90 days         |
| Undrop           | Restore dropped objects                    | `UNDROP TABLE my_table;`             |
| SHOW TABLES      | Lists dropped tables (if within retention) | `SHOW TABLES;`                       |

---

## 🧪 Practice Tip:

Try this:

- Set retention to 3 days
- Drop a table
- Undrop it within the retention window
- Query the table as of a past timestamp (coming in Part 2)

Would you like a **step-by-step worksheet**, **SQL cheat sheet**, or a **timeline diagram** showing how Time Travel works in Snowflake?

Here’s a **detailed and easy-to-understand summary** of **“Time Travel: Part 2”** from the Snowflake course, with practical examples and simplified explanations to help you revise and explain the concept confidently.

---

## 🧠 **Snowflake Time Travel – Part 2 Summary**

### 🎯 **Goal of This Section**:

To learn **three powerful ways** to query past versions of a table using Snowflake’s **Time Travel** feature.

---

## ⏳ **Quick Recap from Part 1**

- **Time Travel** lets you recover or query data from a previous point in time.
- It works based on **retention time**, which is:
  - **1 day by default**
  - Up to **90 days** on Enterprise edition

---

## 🧪 **Setup for Time Travel Demo**

1. **Cloned a table**:

   ```sql
   CREATE OR REPLACE TABLE truck_dev CLONE truck;
   ```

2. **Saved a timestamp and query ID**:

   ```sql
   SET good_data_timestamp = CURRENT_TIMESTAMP;
   SET good_data_query_id = LAST_QUERY_ID;
   ```

3. **Corrupted the data**:
   - Wrong calculation: `year(current_date) / year`
   - Overwrote the `year` column with incorrect values

---

## 🔍 **Three Ways to Query Past Data**

### ✅ 1. **Query as of a Specific Timestamp**

```sql
SELECT *
FROM truck_dev AT (TIMESTAMP => $good_data_timestamp);
```

Or using a literal timestamp:

```sql
SELECT *
FROM truck_dev AT (TIMESTAMP => '2025-09-05 12:00:00'::TIMESTAMP_LTZ);
```

🧠 **Use Case**:

> Recover data as it was at a known time.

---

### ✅ 2. **Query as of N Seconds Ago**

```sql
SELECT *
FROM truck_dev AT (OFFSET => -300);  -- 5 minutes ago
```

🧠 **Use Case**:

> You know roughly when the mistake happened but not the exact timestamp.

---

### ✅ 3. **Query Before a Specific Query Was Run**

```sql
SELECT *
FROM truck_dev BEFORE (STATEMENT => $good_data_query_id);
```

🧠 **Use Case**:

> You want to recover data **before** a specific query (e.g., an update or delete) was executed.

---

## 🧰 **Other Useful Commands**

| Command                                                | Purpose                  |
| ------------------------------------------------------ | ------------------------ |
| `SHOW VARIABLES;`                                      | View all saved variables |
| `SELECT $variable_name;`                               | Display variable value   |
| `ALTER TABLE ... SET DATA_RETENTION_TIME_IN_DAYS = N;` | Change retention window  |

---

## ✅ **Quick Recap Table**

| Method    | Syntax                      | Use Case               |
| --------- | --------------------------- | ---------------------- |
| Timestamp | `AT (TIMESTAMP => ...)`     | Exact time recovery    |
| Offset    | `AT (OFFSET => -N)`         | Relative time recovery |
| Query ID  | `BEFORE (STATEMENT => ...)` | Undo specific query    |

---

## 🧪 Practice Tip:

Try this:

- Clone a table
- Save a timestamp and query ID
- Make a mistake (e.g., wrong update)
- Use all three Time Travel methods to recover the original data

Would you like a **step-by-step worksheet**, **SQL cheat sheet**, or a **visual timeline** showing how Time Travel works in Snowflake?

Here’s a **clear and easy-to-understand summary** of **“Permanent, Transient, and Temporary Tables”** from the Snowflake course, with practical examples and comparisons to help you revise and explain the concept confidently.

---

## 🧠 **Snowflake Table Types – Summary**

### 🎯 **Goal of This Section**:

To understand the **three main types of tables** in Snowflake and how they differ in terms of **retention**, **fail-safe**, and **lifespan**.

---

## 📦 **Types of Tables in Snowflake**

| Table Type    | Retention Period               | Fail-Safe | Lifespan           |
| ------------- | ------------------------------ | --------- | ------------------ |
| **Permanent** | 1–90 days (Enterprise edition) | ✅ 7 days | Until dropped      |
| **Transient** | 0–1 day                        | ❌ None   | Until dropped      |
| **Temporary** | 0–1 day                        | ❌ None   | Until session ends |

---

## 🔍 **Key Differences Explained**

### ✅ 1. **Permanent Tables**

- Default table type (`CREATE TABLE`)
- Can retain historical data for up to **90 days**
- Includes a **7-day fail-safe** period after retention ends
- Best for **critical, long-term data**

### ✅ 2. **Transient Tables**

- Created using `CREATE TRANSIENT TABLE`
- Retention period: **0–1 day**
- **No fail-safe**
- Good for **intermediate or staging data** that doesn’t need long-term recovery

### ✅ 3. **Temporary Tables**

- Created using `CREATE TEMPORARY TABLE`
- Retention period: **0–1 day**
- **No fail-safe**
- Exists **only during your session**
- Ideal for **short-term calculations or scratch work**

---

## 🧪 **Practical Commands Used in the Course**

### ✅ Create Tables

```sql
CREATE TRANSIENT TABLE truck_transient CLONE truck;
CREATE TEMPORARY TABLE truck_temporary CLONE truck;
```

### ✅ Set Retention Period

```sql
ALTER TABLE truck SET DATA_RETENTION_TIME_IN_DAYS = 90;  -- Works for permanent
ALTER TABLE truck_transient SET DATA_RETENTION_TIME_IN_DAYS = 0;  -- Works
ALTER TABLE truck_temporary SET DATA_RETENTION_TIME_IN_DAYS = 0;  -- Works
```

### ✅ Show Retention Info

```sql
SHOW TABLES LIKE 'truck%';
```

---

## 🚨 **Fail-Safe Period**

- **Permanent tables**: 7-day fail-safe after retention ends
- **Transient & Temporary tables**: ❌ No fail-safe
- Fail-safe is **not configurable** and requires Snowflake support to recover data

---

## ✅ **Quick Recap Table**

| Feature                | Permanent         | Transient         | Temporary          |
| ---------------------- | ----------------- | ----------------- | ------------------ |
| Retention (Enterprise) | Up to 90 days     | Max 1 day         | Max 1 day          |
| Fail-Safe              | ✅ Yes (7 days)   | ❌ No             | ❌ No              |
| Lifespan               | Until dropped     | Until dropped     | Until session ends |
| Use Case               | Long-term storage | Intermediate data | Session-only tasks |

---

## 🧪 Practice Tip:

Try this:

- Create one of each table type
- Set and check retention periods
- Drop and observe behavior
- Use `SHOW TABLES` to compare metadata

Would you like a **comparison chart**, **SQL worksheet**, or a **decision guide** to help choose the right table type for different use cases?

Here’s a **detailed and easy-to-understand summary** of the **“Cloning”** feature in Snowflake, based on the course content. This will help you revise and explain the concept confidently.

---

## 🧠 **Snowflake Cloning – Summary**

### 🎯 **Goal of This Section**:

To understand how **cloning** works in Snowflake, how it’s **zero-copy**, and how to use it with **tables, schemas, databases**, and even **Time Travel**.

---

## 🧩 **What is Cloning in Snowflake?**

### ✅ Definition:

**Cloning** creates a **copy of a Snowflake object** (like a table or database) **without duplicating the underlying data** at the time of creation.

🧠 **Think of it like**:

> Making a duplicate that points to the same data until you start changing it.

---

## 📦 **Zero-Copy Cloning**

- When you clone an object:
  - It **shares the same micro-partitions** as the original.
  - **No extra storage** is used initially.
- Once you **modify the clone**, Snowflake starts tracking changes separately.

---

## 🛠️ **Objects You Can Clone**

| Object Type       | Can Be Cloned?        |
| ----------------- | --------------------- |
| Table             | ✅ Yes                |
| Schema            | ✅ Yes                |
| Database          | ✅ Yes                |
| Dynamic Table     | ✅ Yes                |
| Materialized View | ❌ No (not supported) |

---

## 🧪 **Cloning Syntax Examples**

### ✅ Clone a Table

```sql
CREATE OR REPLACE TABLE truck_clone CLONE truck;
```

### ✅ Clone a Schema

```sql
CREATE OR REPLACE SCHEMA raw_pos_clone CLONE raw_pos;
```

### ✅ Clone a Database

```sql
CREATE OR REPLACE DATABASE tasty_bytes_clone CLONE tasty_bytes;
```

---

## 🔍 **Checking Clone Metadata**

Use **Information Schema** to inspect clone relationships and storage:

### ✅ Table Storage Metrics

```sql
SELECT *
FROM INFORMATION_SCHEMA.TABLE_STORAGE_METRICS
WHERE TABLE_NAME IN ('TRUCK', 'TRUCK_CLONE');
```

- `CLONE_GROUP_ID`: Shared between original and clone
- `ACTIVE_BYTES`: Shows storage used by each table

### ✅ Tables View

```sql
SELECT *
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_NAME IN ('TRUCK', 'TRUCK_CLONE');
```

- `BYTES`: Total size (shared initially)
- Updates immediately after changes

---

## 🔁 **Modifying a Clone**

Example: Doubling the clone’s size

```sql
INSERT INTO truck_clone
SELECT * FROM truck;
```

- This increases storage for the **clone only**
- Original table remains unchanged

---

## ⏳ **Cloning with Time Travel**

You can clone an object **as it existed in the past**:

### ✅ Example:

```sql
CREATE OR REPLACE TABLE truck_clone_time_travel
CLONE truck AT (OFFSET => -600);  -- 10 minutes ago
```

- Combines **Time Travel** and **Cloning**
- Useful for restoring historical states

---

## ✅ **Quick Recap Table**

| Feature             | Description                       |
| ------------------- | --------------------------------- |
| Zero-Copy           | No extra storage at creation      |
| Clone Group ID      | Links clone to original           |
| Active Bytes        | Tracks clone’s storage usage      |
| Time Travel + Clone | Clone past version of object      |
| Clone Depth         | You can clone a clone (and so on) |

---

## 🧪 Practice Tip:

Try this:

- Clone a table
- Modify the clone
- Check storage metrics
- Clone a schema or database
- Clone a table using Time Travel

Would you like a **step-by-step worksheet**, **SQL cheat sheet**, or a **diagram** showing clone relationships and storage behavior?

Here’s a **clear and easy-to-understand summary** of the **“Resource Monitors”** section from the Snowflake course, with practical examples and comparisons to help you revise and explain the concept confidently.

---

## 🧠 **Snowflake Resource Monitors – Summary**

### 🎯 **Goal of This Section**:

To understand how to **track and control credit usage** in Snowflake using **resource monitors**—a key tool for cost management and governance.

---

## 📦 **What is a Resource Monitor?**

### ✅ Definition:

A **resource monitor** is a Snowflake object that lets you **set limits** on how many **credits** can be used by:

- The **entire account**
- A **specific warehouse**

🧠 **Think of it like**:

> A budget tracker that can **warn**, **pause**, or **stop** usage when limits are reached.

---

## 🧩 **Types of Resource Monitors**

| Type                | Scope                           | Notes                            |
| ------------------- | ------------------------------- | -------------------------------- |
| **Account-Level**   | Applies to all warehouses       | Only **one** allowed per account |
| **Warehouse-Level** | Applies to a specific warehouse | Multiple allowed                 |

---

## 🔧 **Creating Resource Monitors**

### ✅ Using the UI:

- Go to **Admin > Cost Management > Resource Monitors**
- Click **+ Resource Monitor**
- Set:
  - **Name**
  - **Credit quota** (e.g., 30 credits/day)
  - **Frequency**: Daily, Weekly, Monthly, etc.
  - **Actions**:
    - Notify at 80%
    - Suspend new queries at 100%
    - Suspend running queries at 110%

### ✅ Using SQL:

```sql
CREATE RESOURCE MONITOR tasty_test_rm
WITH CREDIT_QUOTA = 20
FREQUENCY = DAILY
START_TIMESTAMP = IMMEDIATELY
TRIGGERS ON 80 PERCENT DO NOTIFY
TRIGGERS ON 100 PERCENT DO SUSPEND
TRIGGERS ON 110 PERCENT DO SUSPEND IMMEDIATE;
```

---

## 🔗 **Applying to a Warehouse**

```sql
ALTER WAREHOUSE tasty_de_wh
SET RESOURCE_MONITOR = tasty_test_rm;
```

🧠 **Note**:

> You **assign** the monitor to a warehouse using `ALTER WAREHOUSE`, not inside the monitor itself.

---

## 🔍 **Managing Resource Monitors**

| Action            | Command                                                       |
| ----------------- | ------------------------------------------------------------- |
| View all monitors | `SHOW RESOURCE MONITORS;`                                     |
| Modify monitor    | `ALTER RESOURCE MONITOR tasty_test_rm SET CREDIT_QUOTA = 30;` |
| Delete monitor    | `DROP RESOURCE MONITOR tasty_test_rm;`                        |

---

## ✅ **Quick Recap Table**

| Feature            | Description                          |
| ------------------ | ------------------------------------ |
| Credit Quota       | Max credits allowed                  |
| Frequency          | Daily, Weekly, Monthly, etc.         |
| Triggers           | Notify, Suspend, Suspend Immediately |
| Scope              | Account or Warehouse                 |
| Monitor Assignment | Done via `ALTER WAREHOUSE`           |
| Monitoring Start   | Can be immediate or scheduled        |

---

## 🧪 Practice Tip:

Try this:

- Create a resource monitor with a daily quota
- Assign it to a warehouse
- Simulate usage and observe triggers
- Modify and drop the monitor

Would you like a **step-by-step worksheet**, **SQL cheat sheet**, or a **dashboard mockup** to visualize how resource monitors work in Snowflake?

Here’s a **clear and easy-to-understand summary** of **“User-Defined Functions (UDFs): Part 1”** from the Snowflake course, with practical examples and explanations to help you revise and explain the concept confidently.

---

## 🧠 **User-Defined Functions (UDFs) – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand what **UDFs** are in Snowflake, why they’re useful, and how to create a **simple UDF** that returns a scalar value.

---

## 🧩 **What is a UDF?**

### ✅ Definition:

A **User-Defined Function (UDF)** is a **custom SQL function** that you create to **encapsulate logic** you reuse often.

🧠 **Think of it like**:

> A shortcut for a query you keep writing again and again.

---

## 🔧 **Why Use UDFs?**

- Clean up repetitive SQL code
- Improve readability and maintainability
- Customize logic beyond built-in functions

---

## 🛠️ **Creating a Simple UDF**

### ✅ Example: Max Menu Price

Let’s say you often run:

```sql
SELECT MAX(sale_price_usd) FROM menu;
```

Instead, create a UDF:

```sql
USE DATABASE frostbyte_tasty_bytes;

CREATE FUNCTION max_menu_price()
RETURNS NUMBER
AS
$$
  SELECT MAX(sale_price_usd) FROM raw_pos.menu;
$$;
```

### ✅ Using the UDF:

```sql
SELECT max_menu_price();
```

🧠 **Result**:

> Returns the highest menu item price (e.g., \$21)

---

## 🔍 **Viewing UDFs**

### ✅ Show All Functions:

```sql
SHOW FUNCTIONS;
```

- Lists built-in and user-defined functions
- UDFs are marked as **not built-in**
- Shows number of arguments, return type, etc.

---

## 📌 **Key Characteristics of UDFs**

| Feature   | Description                                             |
| --------- | ------------------------------------------------------- |
| Returns   | Always returns a **scalar value**                       |
| Stored In | A **database** (default schema is `public`)             |
| Syntax    | `CREATE FUNCTION ... RETURNS ... AS $$ ... $$;`         |
| Arguments | Can take **zero or more** arguments (covered in Part 2) |

---

## ✅ **Quick Recap Table**

| Task       | Command                                         |
| ---------- | ----------------------------------------------- |
| Create UDF | `CREATE FUNCTION ... RETURNS ... AS $$ ... $$;` |
| Use UDF    | `SELECT function_name();`                       |
| View UDFs  | `SHOW FUNCTIONS;`                               |
| UDF Output | Always scalar (single value)                    |

---

## 🧪 Practice Tip:

Try this:

- Create a UDF that returns the average menu price
- Use `SHOW FUNCTIONS` to verify it
- Call it in a query

Would you like a **step-by-step worksheet**, **SQL cheat sheet**, or a **template** for creating UDFs with arguments (coming in Part 2)?

Here’s a **detailed and easy-to-understand summary** of **“User-Defined Functions (UDFs): Part 2”** from the Snowflake course, with practical examples and explanations to help you revise and explain the concept confidently.

---

## 🧠 **User-Defined Functions (UDFs) – Part 2 Summary**

### 🎯 **Goal of This Section**:

To learn how to create:

- A **SQL UDF with arguments**
- A **Python UDF** in Snowflake

---

## 🧩 **SQL UDF with Arguments**

### ✅ Use Case:

You want to convert the **max menu price** from USD to another currency.

### ✅ Syntax:

```sql
CREATE FUNCTION max_menu_price_converted(usd_to_new NUMBER)
RETURNS NUMBER
AS
$$
  SELECT MAX(sale_price_usd) * usd_to_new FROM raw_pos.menu;
$$;
```

### ✅ Example Usage:

```sql
SELECT max_menu_price_converted(1.35);  -- Converts to CAD
```

🧠 **Result**:

> Returns 28.35 (if max price is \$21)

---

## 🐍 **Python UDF in Snowflake**

### ✅ Use Case:

You want to **winsorize** a value—i.e., cap it within a lower and upper bound.

### ✅ Syntax:

```sql
CREATE FUNCTION winsorize(val FLOAT, upper FLOAT, lower FLOAT)
RETURNS FLOAT
LANGUAGE PYTHON
RUNTIME_VERSION = '3.8'
HANDLER = 'winsorize_func'
AS
$$
def winsorize_func(val, upper, lower):
    if val > upper:
        return upper
    elif val < lower:
        return lower
    else:
        return val
$$;
```

### ✅ Example Usage:

```sql
SELECT winsorize(12, 11, 4);  -- Output: 11
```

🧠 **Explanation**:

- Input value = 12
- Upper bound = 11 → value capped to 11

---

## 🔍 **Key Concepts Recap**

| Concept         | Description                           |
| --------------- | ------------------------------------- |
| SQL UDF         | Custom function written in SQL        |
| Python UDF      | Custom function written in Python     |
| Arguments       | Passed into UDFs to make them dynamic |
| Handler         | Python function name used inside UDF  |
| RUNTIME_VERSION | Specifies Python version (e.g., 3.8)  |

---

## ✅ **Quick Recap Table**

| Task                         | Command                                   |
| ---------------------------- | ----------------------------------------- |
| Create SQL UDF with argument | `CREATE FUNCTION ... (arg TYPE)`          |
| Create Python UDF            | `CREATE FUNCTION ... LANGUAGE PYTHON ...` |
| Call UDF                     | `SELECT function_name(args);`             |
| View UDFs                    | `SHOW FUNCTIONS;`                         |

---

## 🧪 Practice Tip:

Try this:

- Create a SQL UDF that calculates discounted price
- Create a Python UDF that normalizes a value between 0 and 1
- Use `SHOW FUNCTIONS` to verify your UDFs

Would you like a **template**, **worksheet**, or **comparison chart** for SQL vs Python UDFs in Snowflake?

Here’s a **clear and easy-to-understand summary** of **“User-Defined Table Functions (UDTFs)”** from the Snowflake course, with practical examples and explanations to help you revise and explain the concept confidently.

---

## 🧠 **User-Defined Table Functions (UDTFs) – Summary**

### 🎯 **Goal of This Section**:

To understand how to create and use **UDTFs**, which are like UDFs but return **tables** (multiple rows and columns), not just single values.

---

## 🧩 **What is a UDTF?**

### ✅ Definition:

A **User-Defined Table Function (UDTF)** is a custom function that returns a **table** instead of a single scalar value.

🧠 **Think of it like**:

> A reusable query that returns a **dynamic table** based on input parameters.

---

## 🔧 **Creating a UDTF – Example**

### ✅ Use Case:

Return all menu items with a price **above a given threshold**.

### ✅ SQL Syntax:

```sql
CREATE FUNCTION menu_prices_above(price_floor NUMBER)
RETURNS TABLE (item_name VARCHAR, sale_price_usd NUMBER)
AS
$$
  SELECT item_name, sale_price_usd
  FROM raw_pos.menu
  WHERE sale_price_usd > price_floor;
$$;
```

---

## ▶️ **Running a UDTF**

Unlike UDFs, UDTFs are used in the `FROM` clause:

```sql
SELECT *
FROM TABLE(menu_prices_above(15));
```

🧠 **Explanation**:

- `TABLE()` tells Snowflake this function returns rows.
- You can also add filters:

```sql
SELECT *
FROM TABLE(menu_prices_above(15))
WHERE item_name ILIKE '%chicken%';
```

---

## 🔍 **Viewing UDTFs**

### ✅ Show All Functions:

```sql
SHOW FUNCTIONS;
```

- Look for `menu_prices_above`
- Column `IS_TABLE_FUNCTION` = `Y`

---

## 🧪 **Language Support**

| Language   | Supported for UDTFs? |
| ---------- | -------------------- |
| SQL        | ✅ Yes               |
| Python     | ✅ Yes               |
| Java       | ✅ Yes               |
| JavaScript | ✅ Yes               |
| Scala      | ❌ No                |

---

## ✅ **Quick Recap Table**

| Feature   | UDF                 | UDTF                              |
| --------- | ------------------- | --------------------------------- |
| Returns   | Single value        | Table (rows & columns)            |
| Usage     | `SELECT function()` | `SELECT * FROM TABLE(function())` |
| Arguments | Optional            | Optional                          |
| Languages | SQL, Python, etc.   | SQL, Python, etc. (except Scala)  |

---

## 🧪 Practice Tip:

Try this:

- Create a UDTF that returns menu items below a certain calorie count
- Use `TABLE()` to query it
- Add a `WHERE` clause to filter results

Would you like a **template**, **SQL worksheet**, or a **comparison chart** between UDFs, UDTFs, and stored procedures (coming next)?

Here’s a **clear and easy-to-understand summary** of **“Stored Procedures: Part 1”** from the Snowflake course, with practical comparisons and explanations to help you revise and explain the concept confidently.

---

## 🧠 **Stored Procedures – Part 1 Summary**

### 🎯 **Goal of This Section**:

To understand what **stored procedures** are, how they differ from UDFs, and how to view existing procedures in Snowflake.

---

## 🧩 **What is a Stored Procedure?**

### ✅ Definition:

A **stored procedure** is a **saved block of logic** that performs a series of actions (steps), and can be reused.

🧠 **Think of it like**:

> A **script** that you save and run whenever needed.

---

## 🔍 **Stored Procedure vs. UDF**

| Feature     | **Stored Procedure**                                       | **UDF**                         |
| ----------- | ---------------------------------------------------------- | ------------------------------- |
| Returns     | Optional (can return or not)                               | Must return a scalar value      |
| Actions     | Can run DDL & DML (e.g., `CREATE`, `DROP`, `INSERT`)       | Cannot run DDL/DML              |
| Usage       | Called with `CALL procedure_name()`                        | Used inside `SELECT` statements |
| Languages   | SQL (Snowflake Scripting), Python, Java, JavaScript, Scala | Same                            |
| Flexibility | High (loops, branching, control flow)                      | Limited to expressions          |

---

## 🛠️ **Common Use Cases**

- Automating data operations (e.g., creating/dropping tables)
- Running ETL steps
- Sending alerts (e.g., email on failure)
- Managing environments (e.g., switching warehouses)

---

## 📋 **Viewing Existing Procedures**

### ✅ Command:

```sql
SHOW PROCEDURES;
```

- Lists built-in and user-defined procedures
- Example: `SYSTEM$SEND_EMAIL` – sends email notifications

🧠 **Note**:

> Stored procedures are **action-oriented**, unlike UDFs which are **calculation-oriented**.

---

## ✅ **Quick Recap Table**

| Concept             | Description                                                |
| ------------------- | ---------------------------------------------------------- |
| Stored Procedure    | A reusable block of logic that performs actions            |
| Difference from UDF | Can run DDL/DML, doesn’t need to return a value            |
| Languages           | SQL (Snowflake Scripting), Python, Java, JavaScript, Scala |
| View Existing       | `SHOW PROCEDURES;`                                         |

---

## 🧪 Practice Tip:

Try this:

- Run `SHOW PROCEDURES` to explore built-in options
- Think of a task you repeat often (e.g., cleaning a table) and imagine automating it with a stored procedure

Would you like a **template**, **SQL worksheet**, or a **comparison chart** between stored procedures, UDFs, and UDTFs?

Here’s a **detailed and easy-to-understand summary** of **“Stored Procedures: Part 2”** from the Snowflake course, with practical examples and explanations to help you revise and explain the concept confidently.

---

## 🧠 **Stored Procedures – Part 2 Summary**

### 🎯 **Goal of This Section**:

To learn how to **create**, **run**, and **inspect** a stored procedure using **Snowflake Scripting**, and understand how it can automate tasks like deleting old data.

---

## 🧩 **Use Case: Delete Orders Older Than 180 Days**

You worked with the **ORDER_HEADER** table from the Tasty Bytes dataset, which contains:

- `ORDER_ID`
- `ORDER_TS` (timestamp of the order)
- Other metadata

### ✅ Objective:

Create a stored procedure that **automatically deletes** orders older than **180 days** from the most recent order.

---

## 🛠️ **Steps to Build the Stored Procedure**

### ✅ 1. **Explore the Data**

```sql
SELECT MAX(ORDER_TS), MIN(ORDER_TS)
FROM frostbyte_tasty_bytes_clone.raw_pos.order_header;
```

### ✅ 2. **Save Variables**

```sql
SET max_ts = (SELECT MAX(ORDER_TS) FROM order_header);
SET cutoff_ts = (SELECT DATEADD('DAY', -180, $max_ts));
```

### ✅ 3. **Test the Logic**

```sql
SELECT MAX(ORDER_TS)
FROM order_header
WHERE ORDER_TS < $cutoff_ts;
```

---

## 🧪 **Stored Procedure Structure (Snowflake Scripting)**

### ✅ Syntax:

```sql
CREATE OR REPLACE PROCEDURE delete_old()
RETURNS BOOLEAN
LANGUAGE SQL
AS
$$
DECLARE
  max_ts TIMESTAMP;
  cutoff_ts TIMESTAMP;
BEGIN
  LET max_ts = (SELECT MAX(ORDER_TS) FROM order_header);
  LET cutoff_ts = DATEADD('DAY', -180, max_ts);

  DELETE FROM order_header
  WHERE ORDER_TS < cutoff_ts;
END;
$$;
```

---

## ▶️ **Running the Procedure**

### ✅ Call the procedure:

```sql
CALL delete_old();
```

### ✅ Verify the result:

```sql
SELECT MIN(ORDER_TS) FROM order_header;
SELECT $cutoff_ts;
```

---

## 🔍 **Inspecting the Procedure**

### ✅ Show all procedures:

```sql
SHOW PROCEDURES;
```

### ✅ Describe the procedure:

```sql
DESCRIBE PROCEDURE delete_old();
```

- Shows return type, language, and body logic

---

## ✅ **Quick Recap Table**

| Task              | Command                                |
| ----------------- | -------------------------------------- |
| Create procedure  | `CREATE OR REPLACE PROCEDURE ...`      |
| Run procedure     | `CALL procedure_name();`               |
| View procedures   | `SHOW PROCEDURES;`                     |
| Inspect procedure | `DESCRIBE PROCEDURE procedure_name();` |
| Language used     | SQL (Snowflake Scripting)              |

---

## 🧪 Practice Tip:

Try this:

- Create a procedure that archives data older than a year
- Add error handling using `EXCEPTION`
- Use `DECLARE`, `BEGIN`, and `END` blocks

Would you like a **template**, **SQL worksheet**, or a **comparison chart** between stored procedures, UDFs, and UDTFs?
