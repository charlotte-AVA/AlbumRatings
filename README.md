# AlbumRatings

TO-DO List 
1. Plan columns for table (middleware)
2. SDLC, product backlog, User Stories
3. Risk assessment 
4. Backend
5. Front end 


REQUIREMENTS (what is the problem/ Idea?)
MVP:
- I need to be able to review my albumn of the day whilst I am listening to it. 
- I need to record the time, date (BMT) so I can have an ordered log book for reference (and see where/when missing).
- I need to enter the data like an online form. 
- Create, Read, Update and Delete (CRUD) the information in the app. 
- Submission / 'Album of the day' form-update page (component) 
- Listening History / Library / Portfolio / Collection page **ranked by album_id but naturally also date/time**
- Delete button 
Nice Extras: 
- I want an alert at [8pm] if I have not logged an album of the day yet.  
- I want to find images that match the album (via API?)
- ranking the albums by other numeric columns - e.g. **rank**
- ERROR message if an album hs already been logged

TECHNOLOGIES USED 
- Azure Boards - Project Management
- C# / ASP.NET - MVC app
- XUnit - testing
- Git - VCS
- Azure Pipelines - CI/CD
- MySQL (Azure) - databases

CREATING THE TABLES
e.g. -
CREATE TABLE table_name (
  column_name1 data_type(size) constraint_name,
  column_name2 data_type(size) constraint_name,
  PRIMARY KEY (field_name),
  FOREIGN KEY (other_field) REFERENCES table_name(primary_key)
);

1- STRONG ENTITY:
CREATE TABLE Albums (
  album_id INT(3) UNIQUE AUTO_INCREMENT,
  album_name VARCHAR(100) NOT NULL,
  artist VARCHAR(100) NOT NULL,
  decade INT(4) NOT NULL,
  genre VARCHAR(100) DEFAULT 'N/A',
  PRIMARY KEY (album_id)
);

2- WEAK ENTITY:
CREATE TABLE Reviews (
  review_id INT(10) UNIQUE AUTO_INCREMENT,
  fk_album_id INT NOT NULL,
  rating FLOAT(3,2) NOT NULL,
  description VARCHAR(100) DEFAULT 'N/A',
  activity VARCHAR(100) DEFAULT 'N/A',
  date_logged DATETIME UNIQUE,
  PRIMARY KEY (review_id),
  FOREIGN KEY (fk_album_id) REFERENCES Albums(album_id)
);

INSERT
1 - Albums...
INSERT INTO albums (album_name, artist, decade)
    -> VALUES ('Breakfast in America', 'Supertramp', 1980)
    -> ;

INSERT INTO albums (album_name, artist, decade, genre)
    -> VALUES ('Rumours', 'Fleetwood Mac', 1970, 'Rock')
    -> ;

INSERT INTO albums (album_name, artist, decade, genre)
    -> VALUES ("Sgt. Pepper's Lonely Hearts Club Band", 'The Beatles', 1960, 'Rock')
    -> ;

INSERT INTO albums (album_name, artist, decade, genre)
    -> VALUES ('Kind of Blue', 'Miles Davis', 1950, 'Jazz')
    -> ;

INSERT INTO albums (album_name, artist, decade, genre)
    -> VALUES ('OK Computer', 'Radiohead', 1990, 'Rock')
    -> ;

mysql> SELECT * FROM albums;
+----------+---------------------------------------+---------------+--------+-------+
| album_id | album_name                            | artist        | decade | genre |
+----------+---------------------------------------+---------------+--------+-------+
|        1 | Breakfast in America                  | Supertramp    |   1980 | N/A   |
|        2 | Rumours                               | Fleetwood Mac |   1970 | Rock  |
|        3 | Sgt. Pepper's Lonely Hearts Club Band | The Beatles   |   1960 | Rock  |
|        4 | Kind of Blue                          | Miles Davis   |   1950 | Jazz  |
|        5 | OK Computer                           | Radiohead     |   1990 | Rock  |
+----------+---------------------------------------+---------------+--------+-------+
5 rows in set (0.00 sec)



TO-DO:
PLANNING REQUIREMENTS ANALYSIS - identify stakeholders want/needs?
User Story
SDLC
Design - what does the software look like?
UML diagram
