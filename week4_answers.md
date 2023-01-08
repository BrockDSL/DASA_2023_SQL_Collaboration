
# Examples


```SQL 
SELECT "Fiscal year", count(*) from "Emissions" GROUP BY "Fiscal year"
```

```SQL
SELECT "Federal organization", count(*) FROM "Emissions" WHERE "Energy category" LIke "natural gas" GROUP BY "Federal organization" ORDER BY COUNT(*) DESC
```

```SQL
SELECT "Fiscal year", AVG("Energy use (GJ)") from "Emissions" GROUP BY "Fiscal year"
```

```SQL
SELECT * FROM "Emissions" WHERE	"Energy category" LIKE "gasoline"
```

# Questions

## Level 1

*Q1*
How many different Federal Organizations are there in the database? (Display them with counts of how often they appear in the database)

```SQL
SELECT "Federal organization", count(*) FROM "Emissions" GROUP BY "Federal organization" ORDER BY COUNT(*) DESC
```

*Q2*
What are the different values in used in the *Energy category*? (Display them with counts of how often they appear in the database)

```SQL
SELECT "Energy category", count(*) FROM "Emissions" GROUP BY "Federal organization" ORDER BY COUNT(*) DESC
```

*Q3*
What category of *Energy category* has the highest emissions in kilotonne?

```SQL
SELECT "Energy category", SUM("Emissions (kt)") FROM "Emissions" GROUP BY "Federal organization" ORDER BY SUM("Emissions (kt)") DESC
```

*Q4*
What is the average *Emissions* per *Federal Organization*?

```SQL
SELECT "Federal organization", AVG("Emissions (kt)") FROm "Emissions" GROUP BY "Federal organization" ORDER by AVG("Emissions (kt)") DESC
```

*Q5*
What is the average emissions in kilotonnes for the whole datase?

```SQL
SELECT AVG("Emissions (kt)") FROM "Emissions"
```

## Level 2

*Q6*
What is the total emissions from "Health Canada" in the 2005-6 Fiscal year? You can combine multiple LIKE statements with AND

```SQL
SELECT * FROM "Emissions" WHERE "Fiscal year" LIKE "2005-06" and "Federal Organization" LIKE "Health Canada"
```

*Q7*
Display total emissions by *Federal Organizations* if you only consider *fleet* sources. (Order the results from highest to lowest)

```SQL
SELECT "Federal Organization", SUM("Emissions (kt)") FROM "Emissions" WHERE "GHG source" LIKE "fleet" GROUP BY "Federal Organization" ORDER BY SUM("Emissions (kt)") DESC
```

*Q8*
If emissions were fined at 4000\$ a kilotonne what would the total cost be for all of the emissions in this database.

```SQL
SELECT SUM("Emissions (kt)") * 4000 FROM "Emissions"
```

*Q9*
If emissions were fined at 4000\$ a kilotonne which *Federal Organization* would have to pay the most in fines?

```SQL
SELECT "Federal Organization", SUM("Emissions (kt)") * 4000 FROM "Emissions" GROUP BY "Federal Organization" ORDER BY SUM("Emissions (kt)") * 4000 DESC
```

*Q10*
If emissions were fined at 4000\$ a kilotonne which *Fiscal Year* would have the the highest fine?

```SQL
SELECT "Fiscal year", SUM("Emissions (kt)") * 4000 FROM "Emissions" GROUP BY "Fiscal year" ORDER BY SUM("Emissions (kt)") * 4000 DESC
```
