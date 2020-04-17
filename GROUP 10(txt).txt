--===========================================ACTORS TABLE======================================================================


CREATE  TABLE ACTORS
(
    actorId CHAR(4),
    fName VARCHAR2(20) NOT NULL,
    lName VARCHAR2(20) NOT NULL,
    gender VARCHAR2(6) NOT NULL CONSTRAINT CHECK_GENDER CHECK(gender in('Female','Male')),
    birthdate DATE,
    CONSTRAINT PK_ACTOR PRIMARY KEY(actorId)
);


--===========================================MOVIES TABLE======================================================================


CREATE TABLE MOVIES
(
    movieId CHAR(4),
    title VARCHAR2(30) NOT NULL,
    movieType VARCHAR2(20) NOT NULL 
    CONSTRAINT CHK_MOVIE_TYPE CHECK(movieType in('Action','Adventure','Comedy','Drama','Horror','Musical','Thriller','documentary','Romance')),
    releaseDate DATE NOT NULL,
    language VARCHAR2(20) NOT NULL,
    releaseCountry VARCHAR2(30) NOT NULL,
    length_minutes INTEGER NOT NULL,
    rating INTEGER CONSTRAINT CHK_RATING CHECK(rating BETWEEN 1 AND 10),
    CONSTRAINT PK_MOVIES PRIMARY KEY(movieId)
);


--===========================================MOVIEACTOR TABLE======================================================================

CREATE TABLE MOVIEACTOR
(
    actorId CHAR(4),
    movieId CHAR(4),
    CONSTRAINT PK_MOVIEACTOR PRIMARY KEY(actorId,movieId),
    CONSTRAINT FK_ACTORS FOREIGN KEY(actorId) REFERENCES ACTORS(actorId) ON DELETE CASCADE,
    CONSTRAINT FK_MOVIES FOREIGN KEY(movieId) REFERENCES MOVIES(movieId) ON DELETE CASCADE
);


--===========================================DIRECTORS TABLE======================================================================

CREATE TABLE DIRECTORS
(
    directorId CHAR(4),
    fName VARCHAR2(20) NOT NULL,
    lName VARCHAR2(20) NOT NULL,
    CONSTRAINT PK_DIRECTORS PRIMARY KEY(directorId)
);


--===========================================MOVIEDIRECTOR TABLE======================================================================

CREATE TABLE MOVIEDIRECTOR
(
    movieId CHAR(4),
    directorId CHAR(4),
    CONSTRAINT PK_MOVIEDIRECTOR PRIMARY KEY(movieId,directorId),
    CONSTRAINT FK_DMOVIES FOREIGN KEY(movieId) REFERENCES MOVIES(movieId) ON DELETE CASCADE,
    CONSTRAINT FK_DIRECTORS FOREIGN KEY(directorId) REFERENCES DIRECTORS(directorId) ON DELETE CASCADE
);


--===========================================THEATERS TABLE======================================================================

CREATE TABLE THEATERS
(
    theaterId CHAR(4),
    name VARCHAR2(20) NOT NULL,
    PHONE VARCHAR2(10) NOT NULL,
    TOWN VARCHAR2(25) NOT NULL,
    CONSTRAINT PK_THEATERS PRIMARY KEY(theaterId)
);


--===========================================MOVIESHOWTIMES TABLE======================================================================

CREATE TABLE MOVIESHOWTIMES
(
    movieId CHAR(4),
    theaterId CHAR(4),
    showDate DATE NOT NULL,
    STARTTIME VARCHAR2(7) NOT NULL,
    CONSTRAINT PK_MOVIESHOWTIME PRIMARY KEY(movieId,theaterId),
    CONSTRAINT FK_DDMOVIES FOREIGN KEY(movieId) REFERENCES MOVIES(movieId) ON DELETE CASCADE,
    CONSTRAINT FK_THEATERS FOREIGN KEY(theaterId) REFERENCES THEATERS(theaterId) ON DELETE CASCADE
);


==============================================================================================================================================
POPULATING ACTORS TABLE
============================================================================================================================================
INSERT ALL
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC01','Chadwick','Boseman','Male',(TO_DATE('29/11/1977','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC02','Michael','Jordan','Male',(TO_DATE('9/2/1987','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC03','Lupita','Nyongo','Female',(TO_DATE('1/3/1983','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC04','Angela','Basssett','Female',(TO_DATE('16/8/1968','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC05','Gerald','Butler','Male',(TO_DATE('13/11/1969','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC06','James','Jackson','Male',(TO_DATE('6/7/1975','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC07','Pablo','Schrelber','Male',(TO_DATE('26/4/1978','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC08','Evan','Jones','Male',(TO_DATE('1/4/1976','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC09','Gillan','Karen','Female',(TO_DATE('28/11/1987','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC10','Johnson','Dwayne','Male',(TO_DATE('2/5/1972','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC11','Kaya','Scodelario','Female',(TO_DATE('13/3/1992','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC12','Thomas','Brodie','Male',(TO_DATE('16/5/1990','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC13','Allan','Ssali','Male')
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC14','Wilson','Kakule','Male')
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC15','Taraji','Henson','Female',(TO_DATE('11/9/1970','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC16','Billy','Brown','Male',(TO_DATE('30/11/1970','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC17','Jamal','Malik','Male')
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC18','Vikas','Swarup','Male')
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC19','Rima','Kallingal','Female',(TO_DATE('19/1/1984','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC20','Rahdakrishnan','Pathiban','Male')
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC21','Andrea','Calderwood','Male')
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC22','Madina','Nalwanga','Female')
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC23','Joel','Okuyo','Male')
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC24','Cleopatra','Koheirwe','Female',(TO_DATE('15/1/1982','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC25','Michael','Kasaija','Male')
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC26','Natasha','Sinyobye','Female')
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC27','Rosamund','Pike','Female',(TO_DATE('27/1/1979','dd/MM/yyyy')))
INTO ACTORS(actorId,fName,lName,gender) VALUES('AC28','Robert','Kayanja','Male')
INTO ACTORS(actorId,fName,lName,gender,birthdate) VALUES('AC29','Cameroon','Diaz','Female',(TO_DATE('30/8/1972','dd/MM/yyyy')))
SELECT * FROM DUAL;

==============================================================================================================================================
POPULATING MOVIES TABLE
============================================================================================================================================
INSERT ALL
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV01','Black Panther','Action',(TO_DATE('29/1/2018','dd/mm/yyyy')),'English','USA',134,6)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV02','Den of Thieves','Drama',(TO_DATE('19/1/2018','dd/mm/yyyy')),'English','USA',140,7)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV03','Jumanji','Comedy',(TO_DATE('5/12/2017','dd/mm/yyyy')),'English','USA',119,7)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV04','Maze Runner','Action',(TO_DATE('19/9/2014','dd/mm/yyyy')),'English','USA',113,6)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV05','Who Killed Captain Alex?','Action',(TO_DATE('1/1/2010','dd/mm/yyyy')),'Luganda','Uganda',64,8)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV06','Proud Mary','Action',(TO_DATE('12/1/2018','dd/mm/yyyy')),'English','USA',88,5)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV07','SlumDogmillionaire','Drama',(TO_DATE('30/8/2008','dd/mm/yyyy')),'English','United Kingdom',120,8)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV08','Escape from Uganda','Thriller',(TO_DATE('29/11/2013','dd/mm/yyyy')),'Malayalam','India',120,6)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV09','The Last King of Scotland','Thriller',(TO_DATE('27/9/2006','dd/mm/yyyy')),'English','United Kingdom',123,7)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV10','Queen of Katwe','Drama',(TO_DATE('10/9/2016','dd/mm/yyyy')),'English','USA',124,7)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes) VALUES('MV11','State Research Bureau','Action',(TO_DATE('25/1/2011','dd/mm/yyyy')),'English','Uganda',95)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV12','Bala Bala Sese','Drama',(TO_DATE('3/7/2015','dd/mm/yyyy')),'Luganda','Uganda',102,8)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes) VALUES('MV13','7 Days in Entebbe','Thriller',(TO_DATE('9/3/2018','dd/mm/yyyy')),'English','United Kingdom',107)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) VALUES('MV14','God Loves Uganda','documentary',(TO_DATE('18/1/2013','dd/mm/yyyy')),'English','USA',83,7)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) 
VALUES('MV15','Bad Teacher','Comedy',(TO_DATE('24/6/2011','dd/mm/yyyy')),'English','USA',97,5)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes,rating) 
VALUES('MV16','London Has Fallen','Action',(TO_DATE('1/3/2016','dd/mm/yyyy')),'English','USA',99,6)
INTO MOVIES(movieId,title,movieType,releaseDate,language,releaseCountry,length_minutes) VALUES('MV17','A Million Ways to Die in the West ','Comedy',(TO_DATE('30/5/2014','dd/mm/yyyy')),'English','USA',116)
SELECT * FROM DUAL;

ALTER TABLE MOVIES MODIFY TITLE VARCHAR2(35) NOT NULL

==============================================================================================================================================
POPULATING MOVIEACTOR TABLE
============================================================================================================================================
INSERT ALL
INTO MOVIEACTOR(actorId,movieId) VALUES('AC01','MV01')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC02','MV01')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC03','MV01')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC04','MV01')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC05','MV02')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC06','MV02')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC07','MV02')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC08','MV02')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC09','MV03')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC10','MV03')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC11','MV04')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC12','MV04')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC13','MV05')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC14','MV05')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC15','MV06')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC16','MV06')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC17','MV07')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC18','MV07')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC19','MV08')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC20','MV08')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC21','MV09')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC22','MV10')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC03','MV10')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC23','MV11')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC24','MV11')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC25','MV12')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC26','MV12')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC27','MV13')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC28','MV14')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC29','MV15')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC05','MV16')
INTO MOVIEACTOR(actorId,movieId) VALUES('AC08','MV17')
SELECT * FROM DUAL;

==============================================================================================================================================
POPULATING DIRECTORS TABLE
============================================================================================================================================
INSERT ALL
INTO DIRECTORS(directorId,fName,lName) VALUES('DR01','Rayan','Cooler')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR02','Christian','Gudegast')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR03','Jake','Kasdan')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR04','Wes','Ball')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR05','IGG','Nabwana')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR06','Babak','Najafi')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR07','Danny','Boyle')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR08','Rajesh','Nair')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR09','Kevin','Macdonald')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR10','Mira','Nair')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR11','Matt','Bish')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR12','Bashir','Lukyamuzi')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR13','Joe','Padilha')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR14','Roger','Ross')
INTO DIRECTORS(directorId,fName,lName) VALUES('DR15','Seth','MacFarlane')
SELECT * FROM DUAL;
==============================================================================================================================================
POPULATING MOVIEDIRECTOR TABLE
============================================================================================================================================
INSERT ALL
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV01','DR01')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV02','DR02')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV03','DR03')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV04','DR04')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV05','DR05')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV06','DR06')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV07','DR07')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV08','DR08')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV09','DR09')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV10','DR10')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV11','DR11')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV12','DR12')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV13','DR13')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV14','DR14')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV15','DR03')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV16','DR06')
INTO MOVIEDIRECTOR(movieId,directorId) VALUES('MV17','DR15')
SELECT * FROM DUAL;

==============================================================================================================================================
POPULATING THEATERS TABLE
============================================================================================================================================
ALTER TABLE THEATERS MODIFY name VARCHAR2(30);
ALTER TABLE THEATERS MODIFY PHONE VARCHAR2(11);

INSERT ALL
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH01','3D Cinema Magic','041 4240090','Naalya')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH02','Century Cinemax','0700 660415','Kamwokya')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH03','Numax Cinema','041 4668818','Entebbe')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH04','Cinemax','039 2080424','Makerere')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH05','Gayaza Cinema Hall','0702 675838','Gayaza')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH06','SkyeBlue Home Entertainment','0701 900009','Kampala')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH07','WakaliWood','0712 921715','Wakaliga')
INTO THEATERS(theaterId,name,PHONE,TOWN) VALUES('TH08','Roston Theater','0772 615763','Biina')
SELECT * FROM DUAL; 


==============================================================================================================================================
POPULATING MOVIESHOWTIME TABLE
============================================================================================================================================
INSERT ALL
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV01','TH03',(TO_DATE('2/14/2018','MM/DD/YYYY')),'8:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV01','TH01',(TO_DATE('2/14/2018','MM/DD/YYYY')),'7:15 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV01','TH02',(TO_DATE('2/14/2018','MM/DD/YYYY')),'10:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV01','TH04',(TO_DATE('2/14/2018','MM/DD/YYYY')),'09:30 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV02','TH03',(TO_DATE('2/14/2018','MM/DD/YYYY')),'7:45 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV02','TH01',(TO_DATE('2/14/2018','MM/DD/YYYY')),'04:30 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV02','TH02',(TO_DATE('2/14/2018','MM/DD/YYYY')),'07:15 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV02','TH04',(TO_DATE('2/14/2018','MM/DD/YYYY')),'02:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV03','TH01',(TO_DATE('2/14/2018','MM/DD/YYYY')),'02:15 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV03','TH02',(TO_DATE('2/14/2018','MM/DD/YYYY')),'05:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV04','TH01',(TO_DATE('2/14/2018','MM/DD/YYYY')),'02:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV04','TH02',(TO_DATE('2/14/2018','MM/DD/YYYY')),'11:30 AM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV05','TH07',(TO_DATE('2/3/2018','MM/DD/YYYY')),'07:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV04','TH04',(TO_DATE('2/14/2018','MM/DD/YYYY')),'05:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV06','TH01',(TO_DATE('2/14/2018','MM/DD/YYYY')),'07:15 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV07','TH08',(TO_DATE('2/13/2018','MM/DD/YYYY')),'02:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV08','TH06',(TO_DATE('4/5/2018','MM/DD/YYYY')),'11:00 AM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV09','TH04',(TO_DATE('2/3/2018','MM/DD/YYYY')),'4:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV10','TH06',(TO_DATE('2/4/2018','MM/DD/YYYY')),'5:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV11','TH01',(TO_DATE('3/4/2018','MM/DD/YYYY')),'04:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV12','TH05',(TO_DATE('12/3/2018','MM/DD/YYYY')),'7:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV15','TH03',(TO_DATE('12/5/2018','MM/DD/YYYY')),'8:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV13','TH02',(TO_DATE('12/7/2018','MM/DD/YYYY')),'7:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate,STARTTIME) VALUES('MV16','TH06',(TO_DATE('9/2/2018','MM/DD/YYYY')),'9:00 PM')
INTO MOVIESHOWTIMES(movieId,theaterId,showDate) VALUES('MV17','TH08',(TO_DATE('12/6/2018','MM/DD/YYYY')))
SELECT * FROM DUAL;

ALTER TABLE MOVIESHOWTIMES MODIFY STARTTIME VARCHAR2(8) NULL;


NO 1
========================
SELECT phone,town AS "CINEMAX THEATER DETAILS"
FROM THEATERS
WHERE name='Cinemax';

NO 2
========================
SELECT
  EXTRACT( YEAR FROM releasedata) YEAR
FROM Movies
WHERE title ='Escape from Uganda';

NO 3
========================
SELECT * FROM MOVIES
WHERE releaseDate BETWEEN TO_DATE('1/1/2017','DD/MM/YYYY') AND TO_DATE('31/12/2017','DD/MM/YYYY');
--OR
SELECT * FROM MOVIES WHERE TO_CHAR(releaseDate,'YYYY')='2017';
--OR
SELECT *  
FROM Movies
WHERE EXTRACT( YEAR FROM releasedate) = 2017;


NO 4
========================
SELECT title
FROM MOVIES 
WHERE releaseDate BETWEEN TO_DATE('1/1/2016','DD/MM/YYYY') AND TO_DATE('31/12/2018','DD/MM/YYYY');
--OR
SELECT title  
FROM Movies
WHERE EXTRACT( YEAR FROM releasedate)  BETWEEN 2016 AND 2018;

--NO 5
========================
SELECT MOVIES.title,DIRECTORS.fName,DIRECTORS.lName
FROM(( MOVIEDIRECTOR
INNER JOIN MOVIES ON MOVIEDIRECTOR.movieId=MOVIES.movieId)
INNER JOIN DIRECTORS ON MOVIEDIRECTOR.directorId=DIRECTORS.directorId);

--NO 6
========================
SELECT ACTORS.actorId,ACTORS.fName,ACTORS.lName,ACTORS.gender,(TO_CHAR(ACTORS.birthdate,'DD/MM/YYYY')) AS BIRTHDATE,MOVIES.title
FROM  ((MOVIEACTOR
INNER JOIN  ACTORS ON MOVIEACTOR.actorId =ACTORS.actorId)
INNER JOIN MOVIES ON MOVIEACTOR.movieId = MOVIES.movieId)
WHERE MOVIES.title='The Last King of Scotland';


--NO 7
========================
SELECT DIRECTORS.fName,DIRECTORS.lName,MOVIES.title
FROM ((MOVIEDIRECTOR
INNER JOIN DIRECTORS ON MOVIEDIRECTOR.directorId=DIRECTORS.directorId)
INNER JOIN MOVIES ON MOVIEDIRECTOR.movieId=MOVIES.movieId)
WHERE MOVIES.title = (SELECT title FROM MOVIES WHERE title='Queen of Katwe');


--NO 8
========================
SELECT title,TO_CHAR(releaseDate,'DD/MM/YYYY') AS "RELEASEDATE",releaseCountry AS COUNTRY
FROM MOVIES
WHERE NOT releaseCountry  ='USA';


--NO 9
========================
SELECT title,TO_CHAR(releaseDate,'DD/MM/YYYY') AS "RELEASEDATE",releaseCountry AS COUNTRY
FROM MOVIES
WHERE releaseCountry ='Uganda';


NO 10
========================

SELECT MOVIES.title,TO_CHAR(MOVIES.releaseDate,'DD/MM/YYYY') AS RELDATE,DIRECTORS.fName
FROM ((MOVIEDIRECTOR
INNER JOIN  MOVIES ON MOVIEDIRECTOR.movieId = MOVIES.movieId)
INNER JOIN DIRECTORS ON MOVIEDIRECTOR.directorId = DIRECTORS.directorId)
WHERE MOVIES.rating IS NULL; 


NO 11
========================

SELECT MOVIES.title,DIRECTORS.fName AS "FIRST NAME",DIRECTORS.lName AS "LAST NAME"
FROM ((MOVIEDIRECTOR
INNER JOIN  MOVIES ON MOVIEDIRECTOR.movieId =MOVIES.movieId)
INNER JOIN DIRECTORS ON MOVIEDIRECTOR.directorId = DIRECTORS.directorId)
WHERE DIRECTORS.fName ='Jake' AND DIRECTORS.lName ='Kasdan';


NO 12
========================
SELECT EXTRACT(YEAR FROM releaseDate) YEAR,rating FROM MOVIES
WHERE title IS NOT NULL  AND rating >6;
--OR
SELECT
EXTRACT(YEAR FROM releaseDate)YEAR,
COUNT(releaseDate),rating
FROM Movies
WHERE rating > 6
GROUP BY 
EXTRACT(YEAR FROM releaseDate)
HAVING COUNT(releaseData) > = 1 ;



NO 13
========================
SELECT title,EXTRACT(YEAR FROM releaseDate) YEAR,rating,releaseCountry
FROM Movies
WHERE rating = (SELECT max(rating) FROM Movies);

NO 14
========================
SELECT title,EXTRACT(YEAR FROM releaseDate) YEAR,rating,releaseCountry
FROM Movies
WHERE rating = (SELECT min(rating) FROM Movies);

NO:15
========================
SELECT title,EXTRACT(YEAR FROM releaseDate) YEAR,rating
FROM Movies
WHERE rating = (SELECT max(rating) FROM Movies) AND movieType = 'Action';

NO 16
========================
SELECT MOVIES.movieId,MOVIES.title,MOVIES.movieType,MOVIES.releaseDate,
MOVIES.language,MOVIES.releaseCountry,MOVIES.length_minutes,MOVIES.rating
FROM ((MOVIEACTOR
INNER JOIN MOVIES ON MOVIEACTOR.movieId =MOVIES.movieId)
INNER JOIN ACTORS ON MOVIEACTOR.actorId=ACTORS.actorId)
WHERE ACTORS.fName='Lupita' AND ACTORS.lName='Nyongo';


NO 17
========================

SELECT title
FROM MOVIES
WHERE movieId IN('MV04','MV08','MV13');

NO 18
========================
SELECT ACTORS.fName,ACTORS.lName
FROM ((MOVIEACTOR
INNER JOIN ACTORS ON MOVIEACTOR.actorId=ACTORS.actorId)
INNER JOIN MOVIES ON MOVIEACTOR.movieId =MOVIES.movieId)
WHERE MOVIES.title='Jumanji';


NO 19
========================
SELECT ACTORS.fName,ACTORS.lName
FROM ((MOVIEACTOR
INNER JOIN ACTORS ON MOVIEACTOR.actorId=ACTORS.actorId)
INNER JOIN MOVIES ON MOVIEACTOR.movieId =MOVIES.movieId)
WHERE MOVIES.releaseDate < TO_DATE('1/1/2013','DD/MM/YYYY') 
ORDER BY ACTORS.fName,ACTORS.lName;


NO 20
========================

SELECT MOVIES.title,TO_CHAR(MOVIES.releaseDate,'DD/MM/YYYY') AS YEAR,MOVIES.length_minutes AS DURATION ,DIRECTORS.fName,DIRECTORS.lName
FROM ((MOVIEDIRECTOR
INNER JOIN MOVIES ON MOVIEDIRECTOR.movieId =MOVIES.movieId)
INNER JOIN  DIRECTORS ON MOVIEDIRECTOR.directorId = DIRECTORS.directorId)
WHERE MOVIES.releaseDate < '1-JAN-2017'
ORDER BY MOVIES.releaseDate DESC ;


NO 21
========================

SELECT movies.title,movies.length_minutes,EXTRACT(YEAR FROM movies.releaseDate) YEAR,directors.fname,directors.lname
FROM Movies
INNER JOIN movieDirector ON movieDirector.movieId = movies.movieId
INNER JOIN Directors ON movieDirector.directorId = Directors.directorId
WHERE movies.length_minutes = (SELECT MIN(length_minutes) from movies);


NO 22
========================

SELECT DIRECTORS.fName AS "FIRST NAME",DIRECTORS.lName AS "LAST NAME",MOVIES.title
FROM ((MOVIEDIRECTOR
INNER JOIN  DIRECTORS ON MOVIEDIRECTOR.directorId = DIRECTORS.directorId)
INNER JOIN MOVIES ON MOVIEDIRECTOR.movieId =MOVIES.movieId) WHERE MOVIES.rating IS NOT NULL;

NO 23 
========================

SELECT MOVIES.title,ACTORS.fName AS "FIRST NAME",ACTORS.lName AS "LAST NAME"
FROM ((MOVIEACTOR 
INNER JOIN  ACTORS ON MOVIEACTOR.actorId=ACTORS.actorId)
INNER JOIN MOVIES ON MOVIEACTOR.movieId =MOVIES.movieId)
ORDER BY MOVIES.title; 


NO 24
========================
SELECT ACTORS.fName,ACTORS.lName
FROM ((MOVIEACTOR
INNER JOIN ACTORS ON MOVIEACTOR.actorId=ACTORS.actorId)
INNER JOIN MOVIES ON MOVIEACTOR.movieId =MOVIES.movieId)
 WHERE MOVIES.title='Black Panther';


NO 25
========================
SELECT THEATERS.theaterId,THEATERS.name,THEATERS.PHONE,THEATERS.TOWN,MOVIES.title,MOVIES.movieType,MOVIESHOWTIMES.STARTTIME 
FROM(( THEATERS
LEFT OUTER JOIN MOVIESHOWTIMES ON THEATERS.theaterId=MOVIESHOWTIMES.theaterId)
INNER JOIN MOVIES ON MOVIESHOWTIMES.movieId = MOVIES.movieId)
WHERE MOVIESHOWTIMES.showDate=TO_DATE('2/14/2018','MM/DD/YYYY');


NO 26
========================
SELECT MOVIES.title,THEATERS.name AS "THEATER NAME"
FROM (( MOVIESHOWTIMES 
INNER JOIN MOVIES ON MOVIESHOWTIMES.movieId=MOVIES.movieId) 
INNER JOIN THEATERS ON MOVIESHOWTIMES.theaterId= THEATERS.theaterId)
WHERE  THEATERS.name='Gayaza Cinema Hall';


/*NO 27 NOT FINISHED*/
========================
SELECT THEATERS.name,COUNT(MOVIES.movieId)
FROM ((MOVIESHOWTIMES
INNER JOIN THEATERS ON MOVIESHOWTIMES.theaterId =THEATERS.theaterId)
INNER JOIN MOVIES ON MOVIESHOWTIMES.movieId=MOVIES.movieId)
GROUP BY THEATERS.name
HAVING COUNT(MOVIES.movieId) > 5;

NO 28
========================
SELECT THEATERS.name,COUNT(MOVIES.movieId)
FROM ((MOVIESHOWTIMES
INNER JOIN THEATERS ON MOVIESHOWTIMES.theaterId =THEATERS.theaterId)
INNER JOIN MOVIES ON MOVIESHOWTIMES.movieId=MOVIES.movieId)
GROUP BY THEATERS.name;

NO 29
=================


NO 30
========================
SELECT THEATERS.name,MOVIESHOWTIMES.showDate,MOVIESHOWTIMES.STARTTIME
FROM ((MOVIESHOWTIMES
INNER JOIN THEATERS ON MOVIESHOWTIMES.theaterId =THEATERS.theaterId)
INNER JOIN MOVIES ON MOVIESHOWTIMES.movieId=MOVIES.movieId) 
WHERE MOVIES.title ='The Last King of Scotland';
 
PROBLEM 3 NO 1
==========================
SET SERVEROUTPUT ON;
CREATE OR REPLACE PROCEDURE ATMO IS
CURSOR ACTORSOFBIOLOGY IS
SELECT ACTORS.actorId,ACTORS.fName,ACTORS.lName,ACTORS.gender,ACTORS.birthdate,MOVIES.title 
FROM (( MOVIEACTOR
INNER JOIN ACTORS
ON MOVIEACTOR.actorId=ACTORS.actorId)
INNER JOIN MOVIES
ON MOVIEACTOR.movieId =MOVIES.movieId) WHERE MOVIES.title ='Maze Runner';
V_MN ACTORSOFBIOLOGY%ROWTYPE;
BEGIN
FOR V_MN IN ACTORSOFBIOLOGY
LOOP
DBMS_OUTPUT.PUT_LINE(V_MN.fName||'  '||V_MN.lName||'  '||V_MN.gender||'  '||V_MN.birthdate||V_MN.title);
END LOOP;
END ATMO;
/

EXECUTE ATMO;

PROBLEM 3 NO 2
==========================

SET SERVEROUT ON;

DECLARE
CURSOR APP IS
SELECT DIRECTORS.fName,DIRECTORS.lName,MOVIES.title,MOVIES.rating 
FROM (( MOVIEDIRECTOR
INNER JOIN DIRECTORS
ON MOVIEDIRECTOR.directorId=DIRECTORS.directorId)
INNER JOIN MOVIES
ON MOVIEDIRECTOR.movieId =MOVIES.movieId) WHERE MOVIES.rating >7;
DN DIRECTORS.fName%TYPE;
DLN DIRECTORS.lName%TYPE;
MN MOVIES.title%TYPE;
MR MOVIES.rating%TYPE;
BEGIN
OPEN APP;
LOOP
FETCH APP INTO DN,DLN,MN,MR;
EXIT WHEN APP%NOTFOUND;
DBMS_OUTPUT.PUT_LINE('FIRSTNAME:'||DN||' LASTNAME: '||DLN||' '||'MOVIETITLE: '||MN||' '||'MOVIERating: '||MR);
END LOOP;
CLOSE APP;
END;
/


PROBLEM 3 NO 3
==========================
CREATE OR REPLACE TRIGGER MOVIEAFTER
BEFORE INSERT OR UPDATE ON MOVIES
FOR EACH ROW
BEGIN
IF TO_CHAR(:NEW.releaseDate,'YYYY')<'2010' 
THEN IF UPDATING THEN 
RAISE_APPLICATION_ERROR(-20202,'record insertion failed!');
ELSIF INSERTING THEN
RAISE_APPLICATION_ERROR(-20202,'record update failed!');
END IF;
END IF;
END;
/

PROBLEM 3 NO 4
==========================
SET SERVEROUTPUT ON;
CREATE OR REPLACE PROCEDURE TOTALMOVIES(N IN THEATERS.name%TYPE,VB OUT NUMBER) IS
BEGIN
SELECT COUNT(MOVIES.movieId) INTO VB
FROM (( MOVIESHOWTIMES 
INNER JOIN MOVIES ON MOVIESHOWTIMES.movieId=MOVIES.movieId) 
INNER JOIN THEATERS 
ON MOVIESHOWTIMES.theaterId= THEATERS.theaterId) WHERE  THEATERS.name=N;
END;
/
DECLARE
D NUMBER;
N THEATERS.name%TYPE :='SkyeBlue Home Entertainment';
BEGIN
TOTALMOVIES(N,D);
DBMS_OUTPUT.PUT_LINE('TOTAL MOVIES SHOWN: '||D);
END;
/

