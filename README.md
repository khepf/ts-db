# ts-db

## TEAMS
- id
- team_name
- team_number
- team_description
- player_id 
- league_id

## PLAYERS
- id
- player_first_name
- player_last_name
- player_email
- is_team_owner
- player_phone
- team_id
- league_id

## LEAGUES
- id 
- league_name
- league_description
- team_id

## GAMES
- id
- date
- time
- court
- set_1_winner
- set_2_winner
- set_3_winner

### Data Types
#### Numeric Data Types
- INT Whole Numbers (Age, Quantity)
- NUMERIC(P,S) Decimal Numbers (Height, Price)
-SERIAL Auto incrementing Whole Number (Id(Primary Key))
#### String Data Types
- CHAR(N) Fixed length string of length N (Gender, State)
- VARCHAR(N) Varying length string of maximum length N (Name, Email)
- TEXT Varying length string with no maximum length (Comments, Reviews)
#### Time Data Types
- TIME HH:MM:SS
- DATE YYYY-MM-DD (Date of Birth)
- TIMESTAMP (Order Time)
#### Other Data Types
- BOOLEAN True or False (In Stock)
- ENUM A list of values input by the user (Gender)

### Constraints
- UNIQUE
- NOT NULL
- CHECK (Used to check whether values in a column satisfy a specific boolean expression (Age column must contain values greater than 0)

#### Create the Directors Table
CREATE TABLE directors (\
  director_id SERIAL PRIMARY KEY,\
  first_name VARCHAR(30),\
  last_name VARCHAR(30) NOT NULL,\
  date_of_birth DATE,\
  nationality VARCHAR(20)\
);\

#### SELECT * FROM directors;
#### DROP TABLE actors;

#### Create the Actors Table
CREATE TABLE actors (\
  actor_id SERIAL PRIMARY KEY,\
  first_name VARCHAR(30),\
  last_name VARCHAR(30) NOT NULL,\
  gender CHAR(1),\
  date_of_birth DATE\
);\

#### Create the Movies Table (with FK)
CREATE TABLE movies  (\
  movie_id SERIAL PRIMARY KEY,\
  movie_name VARCHAR(50) NOT NULL,\
  movie_length INT,\
  movie_lang VARCHAR(20),\
  release_date DATE,\
  age_certificate VARCHAR(5),\
  director_id INT REFERENCES directors (director_id)\
);\

#### Create the Movie Revenues Table (with FK)
CREATE TABLE movie_revenues  (\
  revenue_id SERIAL PRIMARY KEY,\
  movie_id INT REFERENCES movies (movie_id),\
  domestic_takings NUMERIC(6,2),\
  international_takings NUMERIC(6,2)\
);\

#### Create the linked movies_actors table (Junction Table)
CREATE TABLE movies_actors (\
  movie_id INT REFERENCES movies (movie_id),\
  actor_id INT REFERENCES actors (actor_id),\
  PRIMARY KEY (movie_id, actor_id)\
);\

#### Modify tables and add a column
ALTER TABLE examples\
ADD COLUMN email VARCHAR(50) UNIQUE,\
ADD COLUMN nationality VARCHAR(30),\
ADD COLUMN age INT NOT NULL;\

#### Modify a column's data type
ALTER TABLE examples\
ALTER COLUMN nationality TYPE CHAR(3),\
ALTER COLUMN email TYPE VARCHAR(80);\

#### Insert data into a table
INSERT INTO tablename (first_name, last_name, email, nationality, age)\
VALUES ('David', 'Mitchell', 'dmitchell@gmail.com', 'GBR', 43),\
('Jim', 'Smith', 'jsmith@gmail.com', 'USA', 23)\

#### Update data in a table
UPDATE tablename\
SET email = 'ggg@gmail.com', age = 55\
WHERE example_id = 1;\

#### Delete data from a table
DELETE from tablename\
WHERE example_id = 2\



