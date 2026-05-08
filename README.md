Display all records from the Netflix dataset.

SELECT * FROM mybd.netflix;

Count the total number of Movies in the dataset.

select count(*) from mybd.netflix where type ='Movie';

Count the total number of TV Shows in the dataset.

select count(*) from mybd.netflix where type ='TV Show';

Display the show_id and title for show_id 's1'.

select show_id,title from mybd.netflix where show_id ='s1';

Find the type of the title "Blood & Water".

select type from mybd.netflix where title ='Blood & Water';

List all titles produced in India.

select title from mybd.netflix where country ='India';

Find all titles with rating 'R'.

select title from mybd.netflix where rating ='R';

Display all titles released in the year 2021.

select title from mybd.netflix where release_year ='2021';

List all titles that belong to the "Documentaries" category.

select title from mybd.netflix where listed_in ='Documentaries';

Display all TV Shows whose duration contains "Season".

select show_id, type, title, duration from mybd.netflix where type ='TV Show' and duration like '%season%';

Count the total number of titles by type.

select type, count(*) as total_count from mybd.netflix group by type order by total_count desc;

Count the total number of titles for each rating category.

select rating, count(*) as total_title from mybd.netflix group by rating order by total_title desc;

Display titles with their type and release year sorted by latest release year.

Select title, type, release_year from mybd.netflix where release_year is not null order by release_year desc, title asc;

List all Horror Movies in the dataset.

select show_id,title, listed_in from netflix where listed_in like '%Horror Movies%' and type ='Movie' order by title;

Count the total Kids content grouped by type.

select type, count(*)as total_kids_content from netflix where listed_in like '%Kids%' group by type;

Display all Anime-related titles with their release year.

select title,release_year,listed_in from netflix where listed_in like '%Anime%' order by release_year;

Find all titles where the director information is missing.

select title,type,country from netflix where director is null or director = '' order by type;

Find all titles where cast information is missing.

select title,type from netflix where cast is null or cast = '' order by title;

List all titles containing the word "Naruto".

select title, duration, release_year from netflix where title like '%Naruto%' order by release_year;

Display all titles related to "Jaws".

select title,duration,release_year from netflix	where title like '%Jaws%' order by release_year;

Find the top 5 countries with the highest number of titles.

select country, count(*) as total_titles from netflix where country is not null or country = '' group by country order by total_titles desc limit 5;

Count the total number of titles released each year.

select release_year, count(*) as total_titles from netflix group by release_year order by total_titles desc;

Display all Crime-related TV Shows.

select listed_in, title from netflix where listed_in like '%Crime%' and type ='TV Show'order by title;

List all Reality TV Shows sorted by duration.

select title,duration from netflix where listed_in like '%Reality TV%' and type ='TV Show' order by duration desc;

Find all titles released before the year 2000.

select title,release_year,country from netflix where release_year <2000 order by release_year;

Display all titles added on September 24, 2021.

select title, type , country from netflix where date_added = 'September 24, 2021' order by title;

Count the total number of titles added in September.

select count(*) as total_tittles from netflix where date_added like '%September%' and date_added is not null;

List all family-friendly titles with ratings PG, TV-Y, and TV-G.

select type, title , rating from netflix where rating in('PG','TV-Y', 'TV-G') order by rating,title;

Display all titles produced in the United States.

select title, country, type from netflix where country like '%United States%' order by type, title;

Find all PG-13 Movies released after 2015.

select title , release_year, duration from netflix where type = 'Movie' and rating = 'PG-13' and release_year > 2015 order by release_year desc;

Count the total number of titles available in each country.

select country, count(*) as country_title_total from netflix where country is not null group by country order by country_title_total desc;

Display the latest released titles in the dataset.

select title, release_year from netflix where release_year = (select max(release_year) from netflix ) order by title;

Categorize titles as 'Mature' or 'General' based on rating.

select title , rating, case when rating ='TV-MA' then 'Mature' else 'General' end as 'category' from netflix order by category, title;

Find the oldest released titles in the dataset.

select title, release_year from netflix where release_year = ( select min(release_year) from netflix ) order by title;

Count all Drama-related titles.

select count(*) as drama_count from netflix where listed_in like '%Drama%' or listed_in like '%Dramas%';

Display all Comedy titles with their release year.

select title, release_year from netflix where listed_in like '%Comedies%' order by release_year desc;

Find all titles where country information is missing.

select title, type from netflix where country is null or country ='' order by title;

Find all titles featuring Denzel Washington.

select type, title, cast, release_year from netflix where cast like '%Denzel Washington%' order by release_year;

Find the top 5 countries with the highest number of TV Shows.

select country, count(*) as total_tvshows from netflix where type ='TV Show' and country is not null group	by country order by total_tvshows desc limit 5;

Display all Movies released between 2015 and 2021.

select type, title, release_year from netflix where type = 'Movie' and release_year between 2015 and 2021 order by release_year desc;

Count the total number of titles available in each country.

select country, count(*) as total_titles from netflix where country is not null group by country order by total_titles desc;

Count the total number of titles in each rating category.

select rating, count(*) as total_ratings from netflix where rating is not null group by rating order by total_ratings desc;

Count the total number of titles in each genre category.

select listed_in, count(*) as total_titles from netflix group by listed_in order by total_titles desc;

Find all TV Shows that have exactly one season.

select title, duration from netflix where type ='TV Show' and duration ='1 Season' order by title;

Display Movies directed by more than one director.

select title, director from netflix where director like '%,%' and type ='Movie' order by title;

Find all titles whose description contains the word "family".

select title,description from netflix where description like '%family%';

Categorize titles as 'New' or 'Old' based on release year.

select title, release_year, case when release_year>=2015 then 'New' else 'Old' end as category from netflix order by release_year desc;

Count the total number of Movies and TV Shows released each year.

select release_year,type,  count(*) as total_titles from netflix group by release_year , type order by release_year desc;

Find all titles featuring Adam Sandler.

select title ,cast from netflix where cast like '%Adam Sandler%' order by release_year;

Display titles that belong to both Drama and International Movie categories.

select title, listed_in from netflix where listed_in like '%Dramas%' and listed_in like '%International Movie%' order by title ;
