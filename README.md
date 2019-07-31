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
CREATE TABLE directors (
  director_id SERIAL PRIMARY KEY,
  first_name VARCHAR(30),
  last_name VARCHAR(30) NOT NULL,
  date_of_birth DATE,
  nationality VARCHAR(20)
);
