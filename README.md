# Student Database (Part 1)

A project built as part of freeCodeCamp's Relational Database certification. The goal was to design a normalized PostgreSQL database and write Bash automation scripts to parse CSV files and populate tables dynamically.

## 📁 Repository Contents

- `students.sql` — PostgreSQL dump containing the database schema and table definitions (`majors`, `courses`, `majors_courses`, and `students`).
- `insert_data.sh` — Bash script that parses the CSV files, queries existing primary keys, handles duplicates, and populates the database using `psql`.
- `courses.csv` & `students.csv` — Raw dataset files containing course listings and initial student enrollment records.

## 🛠 Tech Stack

- **Database:** PostgreSQL
- **Scripting:** Bash, Shell
- **CLI Utilities:** `psql`, `cat`, `read`, `cut`

## 🚀 How It Works

1. **Schema Initialization:** The database tables are created with proper relational constraints, foreign keys, and unique checks.
2. **Data Ingestion (`insert_data.sh`):**
   - Reads through `courses.csv` and `students.csv`.
   - Checks if referenced entities (majors, courses) already exist.
   - Inserts new records when missing and fetches their auto-generated IDs.
   - Links relationships accurately in the junction and student tables.

## 🏃 Running Locally

To rebuild and populate the database from scratch:

```bash
# 1. Restore or create the database schema
psql -U postgres -d postgres < students.sql

# 2. Grant execute permissions to the script
chmod +x insert_data.sh

# 3. Run the ingestion script
./insert_data.sh
