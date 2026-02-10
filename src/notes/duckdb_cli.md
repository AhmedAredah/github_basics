`duckdb` - Start DuckDB interactive shell (in-memory database).
`duckdb database.db` - Open or create a persistent database file.
`duckdb :memory:` - Explicitly use in-memory database.
`.tables` - List all tables in current database.
`.schema` - Show schema of all tables (column names and types).
`.mode csv` - Set output format to CSV.
`SELECT * FROM table LIMIT 10;` - Query data from a table.
`.read script.sql` - Execute SQL commands from a file.
`.output file.csv` - Redirect query output to a file.
`.quit` - Exit DuckDB CLI.

# Details
## Connection & Database
`duckdb` - Start interactive session (in-memory).
`duckdb mydb.db` - Open persistent database file (creates if doesn't exist).
`duckdb :memory:` - Explicitly use in-memory database.
`duckdb file.parquet` - Query a Parquet file directly.
`duckdb file.csv` - Query a CSV file directly.

## Navigation & Help
`.tables` - List all tables in database.
`.schema` - Show complete schema (all tables and columns).
`.schema table_name` - Show schema of specific table.
`.help` - Display help for meta-commands.
`.help tables` - Get help on specific command.
`.quit` or `.exit` - Exit DuckDB.

## Query & Data
`SELECT * FROM table;` - Query table (semicolon required).
`SELECT * FROM table LIMIT 10;` - Query first 10 rows.
`SELECT COUNT(*) FROM table;` - Count rows.
`DESC table;` - Show table structure.
`SHOW TABLES;` - List all tables (alternative to .tables).

## Creating & Modifying
`CREATE TABLE table_name (id INT, name VARCHAR);` - Create new table.
`CREATE TABLE new_table AS SELECT * FROM old_table;` - Create table from query.
`INSERT INTO table VALUES (1, 'value');` - Insert data.
`UPDATE table SET column = 'value' WHERE id = 1;` - Update data.
`DELETE FROM table WHERE id = 1;` - Delete data.
`DROP TABLE table_name;` - Delete entire table.
`ALTER TABLE table ADD COLUMN new_col INT;` - Add column.

## Import & Export
`COPY table FROM 'file.csv';` - Import CSV file into table.
`COPY table FROM 'file.parquet';` - Import Parquet file.
`COPY table FROM 'file.json';` - Import JSON file.
`COPY table TO 'file.csv' (FORMAT CSV);` - Export table to CSV.
`COPY (SELECT * FROM table) TO 'file.parquet';` - Export query result to Parquet.
`COPY (SELECT * FROM table) TO 'file.json';` - Export query result to JSON.

## Output Formatting
`.mode csv` - Output as CSV.
`.mode json` - Output as JSON lines.
`.mode parquet` - Output as Parquet.
`.mode table` - Output as formatted table (default).
`.mode list` - Output with custom separator.
`.separator '|'` - Set custom separator for output.
`.output file.txt` - Redirect all output to file.
`.output` - Resume output to console (no file).

## Working with Files
`.read script.sql` - Execute SQL file.
`.read file1.sql file2.sql` - Execute multiple SQL files.
`.import file.csv table_name` - Import CSV into specific table.
`.dump` - Dump entire database as SQL.
`.dump table_name` - Dump specific table as SQL.

## Information
`PRAGMA database_list;` - Show connected databases.
`PRAGMA table_info(table_name);` - Show table column details.
`SELECT COUNT(*) FROM information_schema.tables;` - Count tables in database.
`.version` - Show DuckDB version.
