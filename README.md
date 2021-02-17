```
create table if not exists Singer (
	id serial primary key,
	name varchar(40) not null
);

create table if not exists Genre (
	id serial primary key,
	name varchar(40) not null
);

create table if not exists SingerGenre (
	singer_id integer references Singer(id),
	genre_id integer references Genre(id),
	constraint sg primary key (singer_id, genre_id)
);

create table if not exists Album (
	id serial primary key,
	name varchar(40) not null,
	release date not null,
	singer_id integer references Singer(id)
);

create table if not exists Recording (
	id serial primary key,
	singer_id integer not null references Singer(id),
	album_id integer not null references Album(id)
);

create table if not exists TrackList (
	id serial primary key,
	title varchar(40) not null,
	play_time numeric(3,2),
	album_id integer not null references Album(id)
);

create table if not exists Collection (
	id serial primary key,
	title varchar(40) not null,
	release date not null
);

create table if not exists TrackCollection (
	track_id integer references TrackList(id),
	collection_id integer references Collection(id),
	constraint tc primary key (track_id, collection_id)
);
```
