# DB-Management-System-wk8
# 💧 WASH Surveillance Database

Welcome to the **WASH Surveillance Database** project!  
This database is designed to help track **Water, Sanitation and Hygiene (WASH)** conditions in schools.  
Think of it as a detective’s notebook 🕵️‍♀️ where we record who inspected which school, what they found, and who’s fixing the broken toilets 🚽.

## 📦 What’s inside?
- `wash_surveillance_schema.sql` → Creates the full database schema (tables, views, constraints).
- `wash_surveillance_sample_data.sql` → Fills it with some sample schools, inspectors, inspections, and findings.

## 🛠 Requirements
- **MySQL 8.0+** (important: we’re using window functions like `ROW_NUMBER ()`)
- A command line or GUI client (like MySQL Workbench)
- A sense of curiosity 🔍

## 🚀 How to Run

1. **Clone or download** this project to your computer.  
   ```bash
   git clone https://github.com/yourusername/wash-surveillance-db.git
   cd wash-surveillance-db
2.   Log in to MySQL
mysql -u root -p
(replace root with your MySQL user if different)

3. Run the schema script 🏗️
SOURCE wash_surveillance_schema.sql;
This creates the wash_surveillance database, all tables, constraints, and views.

4. Load sample data 🍿
SOURCE wash_surveillance_sample_data.sql;

5. Explore the database 🔎
Try out some queries:
-- All schools
SELECT * FROM schools;
-- Latest inspection per school (using the view)
SELECT * FROM vw_school_latest_inspection;
-- Schools with broken water sources
SELECT s.name, w.source_type, w.is_functional
FROM schools s
JOIN water_sources w ON s.school_id = w.school_id
WHERE w.is_functional = 0;

🧪** Quick Demo**
After loading sample data, run:
SELECT * FROM vw_school_latest_inspection;
You’ll see each school with its most recent inspection — like a highlight reel of WASH performance 🎬.

🌟 Why is this cool?
Properly normalized schema (goodbye, data duplication 👋).
Supports 1:1, 1:M, and M:M relationships.
Built-in constraints keep your data clean 🧼.

Includes a view to fetch the latest inspection per school instantly.

🎉 Next Steps (Optional Fun)
Add more indicators (e.g., "Soap available at handwashing stations 🧼").
Track repair histories with audit tables.
Connect to a dashboard tool (Metabase, Superset, etc.) for cool visualizations 📊.
Made with ❤️ and a dash of SQL magic ✨
