# ⚽ World Cup Database

A relational database project completed as part of the **freeCodeCamp Relational Database Certification**. This project involves building a PostgreSQL database containing historical data from the FIFA World Cup tournaments since 2014, automating data insertion using a Bash script, and querying the data using advanced SQL.

## 🏆 Certification
I have successfully completed all requirements for this project and earned my official certification:
* **[Verify my freeCodeCamp Relational Database Certification](https://freecodecamp.org)**

---

## 🛠️ Project Structure

The repository consists of the following core components:

*   **`worldcup.sql`**: The complete PostgreSQL database schema dump containing table structures, constraints, and sequences.
*   **`insert_data.sh`**: A Bash script that reads match data from `games.csv` and automatically inserts teams and games into the database, managing foreign key relationships dynamically.
*   **`queries.sh`**: A shell script executing a comprehensive list of SQL queries using aggregations, multi-table `JOIN` statements, and sorting logic to output tournament statistics.
*   **`games.csv`**: The raw data source containing columns for year, round, winner, opponent, winner goals, and opponent goals.

---

## 💾 Database Schema

The database utilizes a clean relational schema consisting of two primary tables connected via foreign keys:

### 1. `teams` Table
*   `team_id`: SERIAL (PRIMARY KEY)
*   `name`: VARCHAR(40) UNIQUE (NOT NULL)

### 2. `games` Table
*   `game_id`: SERIAL (PRIMARY KEY)
*   `year`: INT (NOT NULL)
*   `round`: VARCHAR(40) (NOT NULL)
*   `winner_id`: INT (FOREIGN KEY referencing `teams(team_id)`)
*   `opponent_id`: INT (FOREIGN KEY referencing `teams(team_id)`)
*   `winner_goals`: INT (NOT NULL)
*   `opponent_goals`: INT (NOT NULL)

---

## 🚀 How to Run the Project Locally

If you want to clone this project and run it on your own PostgreSQL instance:

1. **Clone the repository:**
   ```bash
   git clone https://github.com
   cd World-Cup-Database
   ```

2. **Rebuild the database from the SQL dump:**
   ```bash
   psql -U postgres -d postgres < worldcup.sql
   ```

3. **Populate the data using the insertion script:**
   ```bash
   # Make the script executable
   chmod +x insert_data.sh
   # Run the script
   ./insert_data.sh
   ```

4. **Execute the query script to see match statistics:**
   ```bash
   chmod +x queries.sh
   ./queries.sh
   ```

---

## 📊 Sample Output Statistics
Running the `queries.sh` script generates high-level insights directly from the PostgreSQL database, including:
*   Total number of goals scored by winning teams.
*   Average number of goals scored by all winning teams.
*   Most goals scored by a single team in one game.
*   Alphabetical lists of all unique competing teams.
*   The champion teams for each tournament year.
