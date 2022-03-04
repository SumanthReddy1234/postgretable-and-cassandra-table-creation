* creating a postgre table 
* pip install psycopg2

creating a connection to database
---------------------------------
try: 
    conn = psycopg2.connect("host=127.0.0.1 dbname=sumanth user=student password=student")
except psycopg2.Error as e: 
    print("Error: Could not make connection to the Postgres database")
    print(e)
    
try: 
    cur = conn.cursor()
except psycopg2.Error as e: 
    print("Error: Could not get curser to the Database")
    print(e)

conn.set_session(autocommit=True)


try: 
    cur.execute("CREATE TABLE IF NOT EXISTS songs (song_title varchar,artist_name varchar,year int,album_name varchar,single boolean);")
except psycopg2.Error as e: 
    print("Error: Issue creating table")
    print (e)
    
    
try: 
    cur.execute("INSERT INTO songs (song_title ,artist_name ,year ,album_name ,single) \
                 VALUES (%s, %s, %s, %s, %s)", \
                 ("Across The Universe", "The Beatles", "1970", "Let It Be", "False"))
except psycopg2.Error as e: 
    print("Error: Inserting Rows")
    print (e)
    
try: 
    cur.execute("INSERT INTO songs (song_title ,artist_name ,year ,album_name ,single) \
                  VALUES (%s, %s, %s, %s, %s)",
                  ("Think For Yourself", "The Beatles", "1965", "Rubber Soul", "False"))
except psycopg2.Error as e: 
    print("Error: Inserting Rows")
    print (e)
    
    
    
    
