1. List just the titles of all the movies in the database.

SELECT title FROM movie_buff.movies;

2. List the title and year of each movie in the database in DESCENDING order of the year released. (Hint: Combine the SELECT command with the ORDER BY keywords).

select title, year_released from movies order by year_released desc;

3. List all columns for all records of the directors table in ASCENDING alphabetical order based on the director’s country of origin.

select * from directors order by country asc;

4. ORDER BY can also consider multiple columns. List all columns for all records of the directors table in ASCENDING alphabetical order first by the director’s country of origin and then by the director’s last name.

select * from directors order by country asc, last_name asc;

5. Insert a new record into the directors table for Rob Reiner, an American film director.

insert into directors(first_name, last_name, country) values ("Rob", "Reiner", "USA");

6. Combine the SELECT and WHERE keywords to list the last_name and director_id for Rob Reiner.

select last_name, director_id from directors where last_name = "Reiner" and first_name="rob";

7. Insert a new record into the movies table for The Princess Bride, which was released in 1987 and directed by Rob Reiner.

insert into movies(title, year_released, director_id) values("The Princess Bride", 1987, 12);

8. If you list all of the data from the movies table (SELECT * FROM movies;), you will see a column of director ID numbers. This data is not particularly helpful to a user, since they probably want to see the director names instead. Use an INNER JOIN in your SQL command to display a list of movie titles, years released, and director last names.

select movies.title, movies.year_released, directors.last_name from movies inner join directors on movies.director_id = directors.director_id;

9. List all the movies in the database along with the first and last name of the director. Order the list alphabetically by the director’s last name.

select movies.title, directors.first_name, directors.last_name from movies inner join directors on movies.director_id = directors.director_id order by last_name;

10. List the first and last name for the director of The Incredibles. You can do this with either a join or a WHERE command, but for this step please use WHERE.

select first_name, last_name from directors inner join movies on directors.director_id= movies.director_id and movies.title="The Incredibles";

11. List the last name and country of origin for the director of Roma. You can do this with either a join or a WHERE command, but for this step please use a join.

select last_name, country from directors inner join movies on directors.director_id = movies.director_id and movies.title="Roma";

12. Delete a row from the movies table. What consequence does this have on directors? List the contents of both tables to find out.

delete from movies where movie_id=18;

13. Try to delete one person from the directors table. What error results from trying to remove a director?

Cannot delete or update a parent row: a foreign key constraint fails.

Bonus Missions:

1. Note that SQL aliases give a table or column a temporary name. Assign aliases in at least 3 of the items above to make the columns names different and/or more readable in the output.

SELECT title as Movies FROM movie_buff.movies;

2. List all of the movies in the database directed by Peter Jackson.
SELECT title as Movies FROM movie_buff.movies inner join directors on directors.last_name="Jackson"and directors.first_name="Peter";

3. a. Add another column to the movies table that holds the amount of money earned by each film.

alter table movies add column money_earned integer;

Use UPDATE to enter these values for each movie in the database.
3.b. Generate a list that ranks the movie titles based on earnings.

select title from movies order by money_earned asc;

3.c. Generate a list that only shows films that earned above (or below) a certain amount.

select title from movies where money_earned > 100000;

