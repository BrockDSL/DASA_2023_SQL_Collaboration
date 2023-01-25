# Week 4

For this week we are going to convert a CSV file from the Open Data Portal of the Government of Canada.


<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv" target="tutorial">Start</a> the environment and view the Data.


# Examples to Get Ready

Before clicking through, try to read the query and determine what it will do...

**Example 1**

```SQL 
SELECT "Fiscal year", count(*) from "Emissions" GROUP BY "Fiscal year"
```
<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data?sql=SELECT+%22Fiscal+year%22%2C+count%28*%29+from+%22Emissions%22+GROUP+BY+%22Fiscal+year%22" target="tutorial">View in Action</a>


**Example 2**

```SQL
SELECT "Federal organization", count(*) FROM "Emissions" WHERE "Energy category" LIke "natural gas" GROUP BY "Federal organization" ORDER BY COUNT(*) DESC
```
<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data?sql=SELECT+%22Federal+organization%22%2C+count%28*%29+FROM+%22Emissions%22+WHERE+%22Energy+category%22+LIke+%22natural+gas%22+GROUP+BY+%22Federal+organization%22+ORDER+BY+COUNT%28*%29+DESC" target="tutorial">View in Action</a>


**Example 3**

```SQL
SELECT "Fiscal year", AVG("Energy use (GJ)") from "Emissions" GROUP BY "Fiscal year"
```

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data?sql=SELECT+%22Fiscal+year%22%2C+AVG%28%22Energy+use+%28GJ%29%22%29+from+%22Emissions%22+GROUP+BY+%22Fiscal+year%22" target="tutorial">View in Action</a>

**Example 4**

```SQL
SELECT * FROM "Emissions" WHERE	"Energy category" LIKE "gasoline"
```

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data?sql=SELECT+*+FROM+%22Emissions%22+WHERE%09%22Energy+category%22+LIKE+%22gasoline%22" target="tutorial">View in Action</a>


# Questions

Let's try to answer the Level 1 questions during the session. You can try the Level 2 questions on your own. (Answers can be found online, link will be shared in the chat box)

## Level 1

The answers are partially completed... just complete the SQL statement to complete the question. When we share our results in the chat box.

**Q1**
How many different Federal Organizations are there in the database? (Display them with counts of how often they appear in the database)

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q2**
What are the different values in used in the *Energy category*? (Display them with counts of how often they appear in the database)

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q3**
What category of *Energy category* has the highest emissions in kilotonne?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q4**
What is the average *Emissions* per *Federal Organization*?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q5**
What is the average emissions in kilotonnes for the whole datase?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

## Level 2

**Q6**
What is the total emissions from "Health Canada" in the 2005-6 Fiscal year? You can combine multiple LIKE statements with AND

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q7**
Display total emissions by *Federal Organizations* if you only consider *fleet* sources. (Order the results from highest to lowest)

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q8**
If emissions were fined at 4000\$ a kilotonne what would the total cost be for all of the emissions in this database.

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q9**
If emissions were fined at 4000\$ a kilotonne which *Federal Organization* would have to pay the most in fines?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

**Q10**
If emissions were fined at 4000\$ a kilotonne which *Fiscal Year* would have the the highest fine?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>
