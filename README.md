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

Exercise4:
#1
select country.name as "country name", airport.name as "airport name"
from country 
inner join airport on airport.iso_country = country.iso_country
where country.name = "Finland" and scheduled_services = "yes";
![](https://github.com/xind797/database/blob/main/screenshots/4-1.png)

#2
select screen_name, name
from game
inner join airport on airport.ident = game.location;
![](https://github.com/xind797/database/blob/main/screenshots/4-2.png)

#3
select screen_name, country.name
from game 
inner join country on country.iso_country = airport.iso_country
inner join airport on airport.ident = game.location;
![](https://github.com/xind797/database/blob/main/screenshots/4-3.png)

#4
select name, screen_name
from airport
left join game on ident=location
where name like "%Hels%";
![](https://github.com/xind797/database/blob/main/screenshots/4-4.png)

#5
select name, screen_name
from goal
left join goal_reached on goal_id =goal.id
left join game on game.id= game_id;
![](https://github.com/xind797/database/blob/main/screenshots/4-5.png)


Exercise5:
#1
select name
from country
where iso_country in(
select iso_country
from airport
where name like 'Satsuma%'
);
<img width="497" alt="#1(exercise5)" src="https://github.com/user-attachments/assets/27b038c2-cc0e-41bf-a2ce-86de26b04c3d">

#2
select name
from airport
where iso_country in(
select iso_country
from country
where name = 'Monaco'
);
<img width="532" alt="#2(exercise5)" src="https://github.com/user-attachments/assets/cf87e848-9090-4560-8a18-e2a47edd6976">

#3
select screen_name
from game
where id in(
select game_id
from goal_reached
where goal_id in(
select id
from goal
where name = 'CLOUDS')
);
<img width="554" alt="#3(exercise5)" src="https://github.com/user-attachments/assets/45b4dfdb-02ba-4ee9-9ee1-6d7968b29690">


#4
select name
from country
where iso_country not in(
select iso_country
from airport
);
<img width="575" alt="#4(exercise5)" src="https://github.com/user-attachments/assets/87593752-b3e5-4a08-bb4a-b1008d90ac39">


#5
select name
from goal
where id not in(
select goal_id
from goal_reached
where game_id in(
select id
from game
where screen_name = 'Heini'
)
);
<img width="518" alt="#5(exercise5)" src="https://github.com/user-attachments/assets/6a39ff92-cf48-4449-b3c8-33d6a44d15b9">

Exercise6:
#1
select max(elevation_ft)
from airport;
<img width="526" alt="#1(exercise6)" src="https://github.com/user-attachments/assets/de36e9ed-2df6-4627-b31f-28bb62764ffa">

#2
select continent, count(*)
from country
group by continent;
<img width="669" alt="#2(exercise6)" src="https://github.com/user-attachments/assets/347a488c-d8a2-497b-97b2-da8340ff58d6">

#3
select screen_name, count(*)
from game, goal_reached
where id = game_id
group by screen_name;
<img width="533" alt="#3(exercise6)" src="https://github.com/user-attachments/assets/84a44a9e-5f7e-4db2-a18a-7b553c378c87">

#4
select screen_name
from game
where co2_consumed in(
select min(co2_consumed)
from game
);
<img width="564" alt="#4(exercise6)" src="https://github.com/user-attachments/assets/560bfacc-55d4-4f27-86f6-36de73b42499">

#5
select country.name, count(*)
from country, airport
where country.iso_country = airport.iso_country
group by country.iso_country
order by count(*) desc
limit 50;
<img width="770" alt="#5(exercise6)" src="https://github.com/user-attachments/assets/4a697b7b-92d4-43b5-82ee-45bf9efe9aa0">

#6
select country.name
from airport, country
where airport.iso_country = country.iso_country
group by country.iso_country
having count(*) > 1000;
<img width="653" alt="#6(exercise6)" src="https://github.com/user-attachments/assets/41da08e8-4f87-415a-8878-a8e0b69fb683">

#7
select name
from airport
where elevation_ft in(
select max(elevation_ft)
from airport
);
<img width="567" alt="#7(exercise6)" src="https://github.com/user-attachments/assets/f294fba2-69c5-4adb-9437-8334fb9e83dc">

#8
select name
from country
where iso_country in(
select iso_country
from airport
where elevation_ft in(
select max(elevation_ft)
from airport)
);
<img width="581" alt="#8(exercise6)" src="https://github.com/user-attachments/assets/5e3dc7b0-d88c-444a-be5b-ae004df740bb">

#9
select count(*)
from goal_reached,game
where game_id = game.id and
screen_name = 'Vesa'
group by screen_name;
<img width="488" alt="#9(exercise6)" src="https://github.com/user-attachments/assets/e3bb13bd-8512-4cce-97e3-12c9823a7e87">

#10
select name
from airport
where latitude_deg in(
select min(latitude_deg)
from airport
);
<img width="414" alt="#10(exercise6)" src="https://github.com/user-attachments/assets/207efbc0-79b3-46d7-8709-64a3bd678ef1">










