```sql
create table Genre (
	id serial primary key,
	name varchar(20)
);

create table Singer (
	id serial primary key,
	name varchar(20)
);

create table SingerGenre (
	singer_id integer references Singer(id),
	genre_id integer references Genre(id),
	constraint pk primary key (singer_id, genre_id)
);

create table Album (
	id serial primary key,
	name varchar(20),
	pub_year integer
);

create table SingerAlbum (
	singer_id integer references Singer(id),
	album_id integer references Album(id),
	constraint pk1 primary key (singer_id, album_id)
);

create table Collection (
	id serial primary key,
	name varchar(20),
	pub_year integer
);

create table Track (
	id serial primary key,
	name varchar(20),
	duration integer,
	album_id integer references Album(id)
);

create table TrackCollection (
	track_id integer references Track(id),
	collection_id integer references Collection(id),
	constraint pk2 primary key (track_id, collection_id)
);

insert into Genre(name)
values
('pop'),
('rock'),
('jazz'),
('hiphop'),
('indie'),
('blues');

insert into Singer(name) values
('AC/DC'),
('Bon Jovi'),
('Moby'),
('Morgue Vanguard'),
('Da Molotov'),
('Океан Эльзы'),
('Eminem');

insert into SingerGenre(singer_id, genre_id) values
(1, 1), (1, 2), (2, 2), (3, 2), (4, 2), (5, 1), (5, 2), (6, 1), (6, 4);

insert into Album(name, pub_year) values
('Long Ambients 2', 2019), ('Demi Masa', 2018), ('Everything Was Beau', 2018),
('Kamikaze', 2018), ('Con Todo Respeto', 2004), ('Songs of Faith', 1993),
('St. Anger', 2003), ('Back in Black', 1998), ('New Jersey', 1988);

insert into Track(name, duration, album_id) values
('LA12', 2820, 1), ('LA13', 1620, 1), ('LA14', 2340, 1), ('LA15', 1920, 1), ('LA16', 1800, 1),
('LA17', 2520, 1), ('Junta Titimangsa', 139, 2), ('Breakadawn', 275, 2), ('CSDB FM feat. Iwa K', 351, 2),
('Testamen', 297, 2), ('Buckshot Funk', 137, 2), ('Rotasi Baja', 58, 2),
('Di Hadapan Babylon', 266, 2);

insert into Collection(name, pub_year) values
('The White Stripes', 2020), ('RAM Drum &', 2020),
('Neil Young Archives', 2020), ('Kate Bush Remas', 2018),
('John Maus', 2018), ('Civilisation', 2021),
('Limp Pumpo Full', 2021), ('David Bowie A', 2017);

insert into SingerAlbum(singer_id, album_id) values
(5, 1), (6, 2), (5, 3), (7, 4), (7, 5);

insert into TrackCollection(track_id, collection_id) values
(1, 1), (2, 1), (3, 1), (4, 1), (5, 1), (6, 1);

select name, pub_year from album
where pub_year=2018;

select name, duration from Track
order by duration desc
limit 1;

select name, duration from Track
where duration>=210;

select name, pub_year from Collection
where pub_year between 2018 and 2020;

select name from Singer
where name not like '% %';

select * from Track
where name like '%my%' or name like '%мой%';
```
