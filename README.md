# create-a-SQLite-database-connection-to-a-database-that-resides-in-the-memory
import sqlite3

try:
   
    conn = sqlite3.connect(':memory:')
    print("\nMemory database created and connected to SQLite.")

    
    sqlite_select_query = "select sqlite_version();"
    cursor = conn.cursor()
    cursor.execute(sqlite_select_query)

    record = cursor.fetchone()
    print("\nSQLite Database Version is:", record[0])

except sqlite3.Error as error:
    print("\nError while connecting to SQLite:", error)

finally:
    if conn:
        conn.close()
        print("\nThe SQLite connection is closed.")
