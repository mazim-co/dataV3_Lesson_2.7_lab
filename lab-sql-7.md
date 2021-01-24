-- Lab | SQL Queries - Lesson 2.7 Part 1

show variables like 'local_infile';
set global local_infile = 1;

drop table if exists films_2020;

CREATE TABLE `films_2020` (
  `film_id` smallint(5) unsigned NOT NULL AUTO_INCREMENT,
  `title` varchar(255) NOT NULL,
  `description` text,
  `release_year` year(4) DEFAULT NULL,
  `language_id` tinyint(3) unsigned NOT NULL,
  `original_language_id` tinyint(3) unsigned DEFAULT NULL,
  `rental_duration` int(6),
  `rental_rate` decimal(4,2),
  `length` smallint(5) unsigned DEFAULT NULL,
  `replacement_cost` decimal(5,2) DEFAULT NULL,
  `rating` enum('G','PG','PG-13','R','NC-17') DEFAULT NULL,
  PRIMARY KEY (`film_id`),
  CONSTRAINT FOREIGN KEY (`original_language_id`) REFERENCES `language` (`language_id`) ON DELETE RESTRICT ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=1003 DEFAULT CHARSET=utf8;

load data local infile '/Users/mzimmermann/ironhack/week2/dataV3_Lesson_2.7_lab/files_for_part1/films_2020.csv'
into table films_2020;


-- Lab | SQL Queries - Lesson 2.7 Part 2

-- In the table actor, which are the actors whose last names are not repeated? For example if you would sort the data in the table actor by last_name, you would see that there is Christian Arkoyd, Kirsten Arkoyd, and Debbie Arkoyd. These three actors have the same last name. So we do not want to include this last name in our output. Last name "Astaire" is present only one time with actor "Angelina Astaire", hence we would want this in our output list.

-- Which last names appear more than once? We would use the same logic as in the previous question but this time we want to include the last names of the actors where the last name was present more than once

-- Using the rental table, find out how many rentals were processed by each employee.

-- Using the film table, find out how many films were released each year.

-- Using the film table, find out for each rating how many films were there.

-- What is the mean length of the film for each rating type. Round off the average lengths to two decimal places

-- Which kind of movies (rating) have a mean duration of more than two hours?