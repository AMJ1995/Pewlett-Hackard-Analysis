# Analysis Overview

Myself and my colleague Bobby work for Pewlett Hackard and have been given the task by our manager to organize databases since their databases have fallen a bit behind. Using the VsCode software, I created a SQL file that I then applied to the Query Tool in PgAdmin to create different tables with employee and manager data. I then imported CSV files into these tables so that I could begin extracting the data that we need.
For the first deliverable, I was asked to find the number of Pewlett Hackard employees (by title) that are eligible for retirement.
For the second deliverable, I found all of the employees that were eligible for the Mentorship Program offered by our company.

# Deliverable 1

To find the number of employees eligible for retirement, I wrote a SQL code to create a new table called "retirement_titles." This table was to hold all of the employees that were born between January 1, 1952 and December 31, 1955. These are the steps I used to write the code:
* First, I retrieved employee numbers, first names and last names from the Employees table.
* I then retrieved the titles, from dates and to dates from the Titles table.
* Using an INTO clause, I created our new table (retirement_titles)
* I joined both of these tables together (employees and titles) and filtered the table by birth date to find all of the employees born between 1952 and 1955.
* Finally, I exported this table as "retirement_titles.csv"

The SQL code for all of the above steps looks like this:
<img width="560" alt="Screen Shot 2022-04-22 at 2 15 27 PM" src="https://user-images.githubusercontent.com/100390727/164779590-fd0445e0-d203-4cb6-a322-c9e9df827620.png">
Note that I used an inner join to bring these tables together; also, I ordered this data by employee numbers ascending (ASC).

Because some employees have switched titles over the years, I noticed that there were some duplicate entries that I had to get rid of. I removed these duplicates and kept only the most recent title of each employee.
* Using a "DISTINCT ON" statement, I retrieved the first occurence of each employee for each set of rows.
* I then filtered the table by the "to_date" so that I could exclude every employee that has already left the company and therefore shouldn't be considered.
* Then, I put this data into a new table called "Unique_titles" by using an "INTO" clause.
* I sorted this table by employee number (ascending) and to date (descending).
* Finally,  I exported this table as "unique_titles.csv".

The SQL code for these steps look like this:
<img width="427" alt="Screen Shot 2022-04-22 at 2 26 47 PM" src="https://user-images.githubusercontent.com/100390727/164781269-becf137b-16e1-4fe7-8dd3-9d412f6d99bb.png">

Once this part was done, I wrote another query to retrieve the number of employees (by title) who are about to retire.
* First, I retrieved the number of titles from the "unique_titles" table I created above.
* I created a new table called "retiring_titles" using the "INTO" clause.
* I grouped the table by title with "GROUPBY" and sorted the table in descending order by the column count.
* Finally, I exported this table as "retiring_titles.csv".

This Query looked like the following:
<img width="323" alt="Screen Shot 2022-04-22 at 2 31 39 PM" src="https://user-images.githubusercontent.com/100390727/164781931-d3ab0dc5-9934-4f71-a8d3-b58488213494.png">

# Deliverable 2

For this deliverable I needed to find all of the employees eligible for the mentorship program. These employees were to be born between January 1, 1965 and December 31, 1965. I began writing my query to find this information.

* First, I retrieved the employee numbers, first names, last names and birthdates from the employees table.
* Then I retrived the from date and to date from the department employee table and the title column from the titles table.
* I used "DISTINCT ON" to find the first occurence of each employee number for each set of rows.
* I then used the "INTO" clause to create a new table called "mentorship_eligibility".
* I used an "INNER JOIN" to bring together the employees table and the titles table.
* I filtered this table on the to_date as well as on the birth_date columns.
* Finally, I ordered the table by employee numbers and exported this table as "mentorship_eligibility.csv".

This Query looks like the following:
<img width="599" alt="Screen Shot 2022-04-22 at 2 39 25 PM" src="https://user-images.githubusercontent.com/100390727/164782895-a61de241-d661-4d61-ad62-7df4ca74d9ca.png">

*note that all of these exported CSV files are included in this repository.

# Results of Deliverables 1 & 2

Upon completing these deliverables I was able to successfuly analyze the number of employees who are eligible to retire as well as those who are eligible for the mentorship program. Here are some major points I'd like to share:

* There is a very high percentage of employees who are eligible to retire (64%). There are 29,414 Engineers as well as 28,254 Senior Staff members who are eligible. This is a large percentage of the overall employees of Pewlett Hackard.
* Here is an image showing the 20 employees eligible for the mentorship program:
* <img width="783" alt="Screen Shot 2022-04-22 at 2 55 34 PM" src="https://user-images.githubusercontent.com/100390727/164785008-d94b86be-d81b-46f2-8cce-c1b4451a945b.png">
* There is a total of 1,940 employees eligible for the mentorship program.
* These employees all have titles of either Staff, Senior Staff, Engineer, Senior Engineer or Technique Leader.

# Summary

I was able to successfuly find the number of elegible retirees as well as the number of employees qualified for the mentorship program. I don't feel very positive about these results and I feel as if there is a major problem brewing for Pewlett Hackard. As I stated above, 64% of employees (57,668) are elegible to retire. This is a huge problem because if all of these employees were to retire and leave, there would need to be some major hiring. There are only 1,940 employees who are able to be mentors and do all of the training for new hires. If everyone were to retire within the next year or two, and around 55,000 people were hired to take their places, I do not believe that this very low number of mentors would be able to handle all of this training. I hope that Pewlett Hackard is able to use my findings to make decisions that will help them when these employees decide to leave the company. All in all, I was able to use SQL to help this company analyze this crucial data.

