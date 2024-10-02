SELECT COUNT(*) FROM WineQuality;
Check for Null or Missing Values:


SELECT * FROM WineQuality WHERE fixed_acidity IS NULL OR volatile_acidity IS NULL;
Step 2: Descriptive Statistics
Now, start calculating descriptive statistics for the different columns.

Average, Minimum, and Maximum for alcohol:

SELECT MIN(alcohol), MAX(alcohol), AVG(alcohol) FROM WineQuality;
Average and Standard Deviation for fixed_acidity:

SELECT AVG(fixed_acidity), STDEV(fixed_acidity) FROM WineQuality;
Step 3: Group By Analysis
Group the wines by quality rating to analyze differences across various attributes.

Average Values of Features Based on Quality:

SELECT quality, AVG(alcohol) AS avg_alcohol, AVG(fixed_acidity) AS avg_acidity
FROM WineQuality
GROUP BY quality
ORDER BY quality DESC;
Count Wines by Quality Rating:

SELECT quality, COUNT(*) AS count_of_wines
FROM WineQuality
GROUP BY quality
ORDER BY quality DESC;
Step 4: Filter High-Quality Wines
Focus on higher quality wines (e.g., wines with a quality score of 7 or higher).

Retrieve High-Quality Wines:

SELECT * FROM WineQuality WHERE quality >= 7;
Average Alcohol Content for High-Quality Wines:

SELECT AVG(alcohol) FROM WineQuality WHERE quality >= 7;
Step 5: Correlation Analysis
Use SQL to explore potential correlations between wine quality and different features.

Check Correlation Between Alcohol and Quality:


SELECT quality, AVG(alcohol) AS avg_alcohol
FROM WineQuality
GROUP BY quality
ORDER BY quality;
Identify Attributes That Vary Significantly Across Quality Levels:

SELECT quality, AVG(fixed_acidity), AVG(citric_acid), AVG(alcohol)
FROM WineQuality
GROUP BY quality
ORDER BY quality;

sql
Copy code
SELECT quality, alcohol,
       AVG(alcohol) OVER (PARTITION BY quality ORDER BY alcohol) AS moving_avg_alcohol
FROM WineQuality;
