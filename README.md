Exercise2:
#1
select* from goal;
![](https://github.com/xind797/database/blob/main/1.png)

#2
select name, type from airport where iso_country = 'FI';
![](https://github.com/xind797/database/blob/main/2.png)

#3
select name from airport where iso_country = 'FI' order by name;
![](https://github.com/xind797/database/blob/main/3.png)

#4
select name, type from airport where iso_country = 'FI' order by type, name;
![](https://github.com/xind797/database/blob/main/4.png)

#5
select name from country where name like 'F%';
![](https://github.com/xind797/database/blob/main/5.png)

#6
select name from country where name like '%F%';
![](https://github.com/xind797/database/blob/main/6.png)

#7
select location from game where screen_name = 'Vesa' ;
![](https://github.com/xind797/database/blob/main/7.png)

#8
select co2_consumed from game where screen_name = 'Ilkka';
![](https://github.com/xind797/database/blob/main/8.png)

#9
select distinct co2_budget from game;
![](https://github.com/xind797/database/blob/main/9.png)

#10
SELECT screen_name, co2_budget, co2_consumed, @co2_left := (co2_budget - co2_consumed) AS co2_left FROM game WHERE screen_name = 'Ilkka';
![](https://github.com/xind797/database/blob/main/10.png)

Exercise3:
#1
select country.name as "country name", airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "Iceland";
![](https://github.com/xind797/database/blob/main/screenshots/3-1.png)

#2
select airport.name as 'airport name'
from airport, country
where airport.iso_country = country.iso_country and
country.name = 'France' and
airport.type = 'large_airport';
![](https://github.com/xind797/database/blob/main/screenshots/3-2.png)

#3
select country.name as country_name, airport.name as airport_name
from country, airport
where airport.iso_country = country.iso_country and country.continent = 'AN';
![](https://github.com/xind797/database/blob/main/screenshots/3-3.png)

#4
select elevation_ft 
from airport, game
where game.location = airport.ident and screen_name = 'Heini';
![](https://github.com/xind797/database/blob/main/screenshots/3-4.png)

#5
select elevation_ft * 0.3048 as elevation_m 
from airport, game
where game.location = airport.ident and screen_name = 'Heini';
![](https://github.com/xind797/database/blob/main/screenshots/3-5.png)

#6
select name
from airport, game
where game.location = airport.ident and screen_name = 'Ilkka';
![](https://github.com/xind797/database/blob/main/screenshots/3-6.png)

#7
select country.name
from airport, game, country
where game.location = airport.ident and country.iso_country=airport.iso_country and
screen_name = 'Ilkka';
![](https://github.com/xind797/database/blob/main/screenshots/3-7.png)

#8
select name
from game, goal, goal_reached
where goal_id = goal.id and game_id =game.id and screen_name = 'Heini';
![](https://github.com/xind797/database/blob/main/screenshots/3-8.png)

#9
select airport.name
from airport, goal, goal_reached, game
where airport.ident=game.location 
and goal_id = goal.id 
and game_id =game.id 
and screen_name = 'Ilkka';
![](https://github.com/xind797/database/blob/main/screenshots/3-9.png)

#10
select country.name
from airport, country, goal, goal_reached, game
where airport.ident=game.location 
and country.iso_country = airport.iso_country
and goal_id = goal.id 
and game_id =game.id 
and screen_name = 'Ilkka';
![](https://github.com/xind797/database/blob/main/screenshots/3-10.png)
















