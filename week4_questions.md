![dsl_logo](dsl_logo.png)


# SQL Workshop - Week 4

We've spent 3 weeks looking at the Northwind database and developing our understanding of how to build complex queries involving multiple tables. We also used the Franchise app to explore an SQLite file.

Today we are going to changes things a bit and look at a different data set, using a different SQL client.

## The Data

<a href="https://open.canada.ca/data/en/dataset/6bed41cd-9816-4912-a2b8-b0b224909396" target="_blank">Government of Canada’s Greenhouse Gas Emissions Inventory</a>

We'll be using a modified version of table 5.


## The Environment

We'll be using a platform called <a href="https://datasette.io/" target="_blank">Datasette</a> that is full featured set of tools that allows you to explore data from spreadsheets and turn them into SQL. We are using a web-based version of this called <a href="https://lite.datasette.io/" target="_blank">Datasette Lite</a>

# Let's begin

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

Let's try to answer the Level 1 questions during the session. 


## Level 1

The answers are partially completed... Submit the SQL query that you wrote to answer the question in each question's form.

**Q1**
How many different Federal Organizations are there in the database? (Display them with counts of how often they appear in the database)

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

<a target="_blank" href="https://forms.office.com/r/HinRDcvLjZ">Submit your answer</a>

**Q2**
What are the different values in used in the *Energy category*? (Display them with counts of how often they appear in the database)

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

<a target="_blank" href="https://forms.office.com/r/6FsfJ06fNd">Submit your answer</a>

**Q3**
What category of *Energy category* has the highest emissions in kilotonne?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

<a target="_blank" href="https://forms.office.com/r/kwxg1Ug85u">Submit your answer</a>

**Q4**
What is the average *Emissions* per *Federal Organization*?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

<a target="_blank" href="https://forms.office.com/r/qFkhf1rUPE">Submit your answer</a>

**Q5**
What is the average emissions in kilotonnes for the whole data set?

<a href="https://lite.datasette.io/?csv=https://raw.githubusercontent.com/BrockDSL/DASA_2023_SQL_Collaboration/main/Emissions.csv#/data" target="tutorial">Try This question</a>

<a target="_blank" href="https://forms.office.com/r/n8DwhP3XYp">Submit your answer</a>

## Level 2

Submit all of your answer for Level 2 questions directly in this <a href="https://forms.office.com/r/Qcdjm9rMeT" target="_blank">form</a>. Just submit the SQL query that you wrote to answer the question.

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
