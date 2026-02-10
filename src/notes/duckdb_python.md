`import duckdb` - Import DuckDB library.
`duckdb.sql("SELECT * FROM table")` - Execute SQL query on in-memory database.
`conn = duckdb.connect("database.db")` - Connect to persistent database file.
`result = conn.execute("SELECT * FROM table")` - Execute query on connection.
`result.df()` - Convert query result to pandas DataFrame.
`duckdb.from_df(df)` - Create DuckDB relation from pandas DataFrame.
`duckdb.from_arrow(arrow_table)` - Create DuckDB relation from Arrow table.
`duckdb.from_parquet("file.parquet")` - Load Parquet file into DuckDB.
`result.fetchall()` - Fetch all rows as list of tuples.
`conn.close()` - Close database connection.

# Details
## Connection & Setup
`import duckdb` - Import DuckDB module.
`conn = duckdb.connect()` - Create in-memory connection.
`conn = duckdb.connect("database.db")` - Create/open persistent database.
`conn = duckdb.connect(":memory:")` - Explicitly use in-memory.
`duckdb.sql()` - Quick query on default in-memory database (no connection needed).
`conn.close()` - Close connection and release resources.

## Executing Queries
`conn.execute("SELECT * FROM table").fetchall()` - Execute and fetch all results.
`conn.execute("SELECT * FROM table").fetchone()` - Fetch first row only.
`conn.execute("SELECT * FROM table LIMIT 10")` - Query with limit.
`result = conn.execute("SELECT COUNT(*) FROM table")` - Store result object.
`conn.execute("CREATE TABLE table_name (id INT, name VARCHAR)")` - Create table.
`conn.execute("INSERT INTO table VALUES (1, 'value')")` - Insert row.

## Converting Results
`result.df()` - Convert result to pandas DataFrame.
`result.arrow()` - Convert result to Arrow table.
`result.pl()` - Convert result to Polars DataFrame.
`result.fetchall()` - Get all rows as list of tuples.
`result.fetchone()` - Get first row as tuple.
`result.fetchmany(5)` - Get 5 rows as list of tuples.

## Working with DataFrames
`duckdb.from_df(df)` - Create relation from pandas DataFrame.
`duckdb.from_df(df).execute("SELECT * WHERE col > 10")` - Query DataFrame directly.
`duckdb.sql("SELECT * FROM df")` - Query DataFrame by name in SQL.
`result = conn.execute("SELECT * FROM df").df()` - Execute and convert to DataFrame.
`df.to_sql("table_name", conn)` - Write pandas DataFrame to DuckDB table.

## Working with Arrow & Polars
`duckdb.from_arrow(arrow_table)` - Create relation from Arrow table.
`duckdb.from_arrow(arrow_table).execute("SELECT *")` - Query Arrow table.
`duckdb.from_df(pl_df)` - Create relation from Polars DataFrame.
`result.arrow()` - Convert result to PyArrow table.
`result.pl()` - Convert result to Polars DataFrame.

## Import & Export
`duckdb.from_parquet("file.parquet")` - Load Parquet file.
`duckdb.from_csv("file.csv")` - Load CSV file.
`duckdb.from_json("file.json")` - Load JSON file.
`conn.execute("COPY table TO 'file.parquet'")` - Export to Parquet.
`conn.execute("COPY table TO 'file.csv'")` - Export to CSV.
`result.write_parquet("file.parquet")` - Write result to Parquet file.

## Transactions
`conn.begin()` - Start transaction.
`conn.commit()` - Commit transaction.
`conn.rollback()` - Rollback transaction.
`with conn.begin():` - Context manager for automatic commit/rollback.

## Metadata & Inspection
`conn.execute("SELECT * FROM information_schema.tables").fetchall()` - List tables.
`conn.execute("PRAGMA table_info(table_name)").fetchall()` - Get table schema.
`conn.execute("SHOW TABLES").fetchall()` - List all tables.
`conn.execute("DESC table_name").fetchall()` - Describe table.

## Example Workflow
```python
import duckdb
import pandas as pd

# Create connection
conn = duckdb.connect("my_database.db")

# Create table from DataFrame
df = pd.DataFrame({"id": [1, 2, 3], "name": ["Alice", "Bob", "Charlie"]})
conn.execute("CREATE TABLE users AS SELECT * FROM df")

# Query
result = conn.execute("SELECT * FROM users WHERE id > 1").df()

# Export
conn.execute("COPY users TO 'users.parquet'")

# Close
conn.close()
```
