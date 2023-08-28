# SQL Temelleri

> Bu repo [Patika.Dev](https://academy.patika.dev/tr/paths) SQL eğitimindeki ödevler için oluşturulmuştur.

>Bu repo'da sadece 1 adet README dosyası vardır.
## Ödev Listesi
>ödevler eklenmeye devam edecektir.
* **SQL Ödev 1** : *WHERE ve Mantıksal Operatörler*
* **SQL Ödev 2** : *BETWEEN ve IN*
* **SQL Ödev 3** : *LIKE ve ILIKE*
* **SQL Ödev 4** : *DISTINCT ve COUNT*
* **SQL Ödev 5** : *ORDER BY & LIMIT ve OFFSET*
* **SQL Ödev 6** : *AGGREGATE Fonksiyonlar*
* **SQL Ödev 7** : *GROUP BY & HAVING*
* **SQL Ödev 8** : *Tablo Oluşturmak - Verileri Güncellemek - Silmek*


## SQL Ödev 1 | *WHERE ve Mantıksal Operatörler* - *Soru ve cevapları*

1. **film** tablosunda bulunan **title** ve **description** sütunlarındaki verileri *sıralayınız*.

```
SELECT title, description FROM film;
```

2. **film** tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (**length**) *60* dan büyük **VE** *75* ten küçük olma koşullarıyla *sıralayınız*.

```
SELECT * FROM film
WHERE length > 60 AND length < 75;
```

3. **film** tablosunda bulunan tüm sütunlardaki verileri **rental_rate** *0.99* **VE** **replacement_cost** *12.99* **VEYA** *28.99* olma koşullarıyla *sıralayınız*.

```
SELECT * FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99
OR replacement_cost = 28.99;
```

4. **customer** tablosunda bulunan **first_name** sütunundaki değeri ***'Mary'*** olan müşterinin **last_name** sütunundaki değeri *nedir?*

```
SELECT last_name FROM customer
WHERE  first_name = 'Mary';
```

5. **film** tablosundaki uzunluğu(**length**) *50* ten büyük ***OLMAYIP*** aynı zamanda **rental_rate** değeri *2.99* **veya** *4.99* ***OLMAYAN*** verileri *sıralayınız*.

```
SELECT * FROM film
WHERE length <= 50
AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);
```

## SQL Ödev 2 | *BETWEEN ve IN* - *Soru ve cevapları*

1. **film** tablosunda bulunan tüm sütunlardaki verileri **replacement_cost** değeri *12.99* dan büyük eşit ve *16.99* küçük olma koşuluyla *sıralayınız*. *( BETWEEN - AND yapısını kullanınız.)*

```
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

2. **.actor** tablosunda bulunan **first_name** ve **last_name** sütunlardaki verileri **first_name** *'Penelope'* **veya** *'Nick'* **veya** *'Ed'* değerleri olması koşuluyla *sıralayınız.* *( IN operatörünü kullanınız.)*

```
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```

3. **film** tablosunda bulunan tüm sütunlardaki verileri **rental_rate** *0.99*, *2.99*, *4.99* **VE** **replacement_cost** *12.99*, *15.99*, *28.99* olma koşullarıyla *sıralayınız.* *( IN operatörünü kullanınız.)*

```
SELECT * FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99)
AND replacement_cost IN (12.99, 15.99, 28.99);
```
## SQL Ödev 3 | *LIKE ve ILIKE* - *Soru ve cevapları* 

1. **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden *'A'* karakteri ile başlayıp *'a'* karakteri ile sonlananları *sıralayınız.*

```
SELECT country FROM country
WHERE country LIKE 'A%a';
```

2. **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden en az *6* karakterden oluşan ve sonu *'n'* karakteri ile sonlananları *sıralayınız.*

```
SELECT country FROM country
WHERE country LIKE '_____n';
```

3. **film** tablosunda bulunan **title** sütunundaki **film** isimlerinden en az *4* adet büyük ya da küçük harf farketmesizin *'T'* karakteri içeren **film** isimlerini *sıralayınız.*

```
SELECT title FROM film
WHERE title ILIKE '%T%T%T%T';
```

4. **film** tablosunda bulunan tüm sütunlardaki verilerden **title** *'C'* karakteri ile başlayan ve uzunluğu (**length**) *90* dan büyük olan ve **rental_rate** *2.99* olan verileri *sıralayınız.*

```
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99; 
```

## SQL Ödev 4 | *DISTINCT ve COUNT* - *Soru ve cevapları* 

1. **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden **farklı**++ değerleri *sıralayınız*.

```
SELECT DISTINCT replacement_cost FROM film;
```

2. **film** tablosunda bulunan **replacement_cost** sütununda birbirinden **farklı** kaç tane veri *vardır?*

```
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```

3. **film** tablosunda bulunan film isimlerinde (**title**) kaç tanesini *T* karakteri ile başlar ve aynı zamanda **rating** '*G*' ye *eşittir?*

```
SELECT COUNT (title) FROM film
WHERE title LIKE 'T%' AND rating ='G';
```

4. **country** tablosunda bulunan ülke isimlerinden (**country**) kaç tanesi *5* karakterden *oluşmaktadır?*

```
SELECT COUNT(country) FROM country
WHERE country LIKE '_____';
```

5. **city** tablosundaki şehir isimlerinin kaç tanesi '*R*' veya '*r*' karakteri ile *biter?*

```
SELECT COUNT(city) FROM city
WHERE city ILIKE '%r';
```

## SQL Ödev 5 | *ORDER BY & LIMIT ve OFFSET* - *Soru ve cevapları* 

1. **film** tablosunda bulunan ve film ismi (**title**) *'n'* karakteri ile biten en uzun (**length**) *5* filmi *sıralayınız*.

```
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

2. **film** tablosunda bulunan ve film ismi (**title**) *'n'* karakteri ile biten en kısa (**length**) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) *sıralayınız*.


```
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length
OFFSET 5
LIMIT 5;
```

3. **customer** tablosunda bulunan **last_name** sütununa göre azalan yapılan sıralamada **store_id** *1* olmak koşuluyla *ilk 4* veriyi *sıralayınız*.


```
SELECT * FROM customer
WHERE store_id = '1' 
ORDER BY last_name DESC
LIMIT 4;
```

## SQL Ödev 6 | *AGGREGATE Fonksiyonlar* - *Soru ve cevapları*

1. **film** tablosunda bulunan **rental_rate** sütunundaki değerlerin *ortalaması* *nedir?*

```
SELECT ROUND(AVG(rental_rate),2) FROM film;
```

2. **film** tablosunda bulunan filmlerden *kaç tanesi* *'C'* karakteri ile *başlar?*

```
SELECT COUNT(title) FROM film 
WHERE title LIKE 'C%';
```

3. **film** tablosunda bulunan filmlerden **rental_rate** değeri *0.99* a eşit olan en uzun (**length**) film *kaç dakikadır?*

```
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```

4. **film** tablosunda bulunan filmlerin **uzunluğu** *150* dakikadan büyük olanlarına ait kaç farklı **replacement_cost** değeri *vardır?*

```
SELECT COUNT(DISTINCT replacement_cost ) FROM film
WHERE length > 150;
```

## SQL Ödev 7 | *GROUP BY & HAVING* - *Soru ve cevapları*

1. **film** tablosunda bulunan filmleri **rating** değerlerine göre *gruplayınız.*

```
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
```

2. **film** tablosunda bulunan filmleri **replacement_cost** sütununa göre **grupladığımızda** film sayısı *50* den fazla olan **replacement_cost** değerini ve karşılık gelen *film sayısını sıralayınız.*


```
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost 
HAVING COUNT(*) > 50;
```

3. **customer** tablosunda bulunan **store_id** değerlerine karşılık gelen *müşteri sayılarını nelerdir?*

```
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```

4. **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre **gruplandırdıktan** sonra *en fazla şehir sayısı* barındıran **country_id** bilgisini ve şehir sayısını *paylaşınız.*

```
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY country_id DESC
LIMIT 1;
```

## SQL Ödev 8 | *Tablo Oluşturmak - Verileri Güncellemek - Silmek* - *Soru ve cevapları*

1. **test** veritabanınızda **employee** isimli sütun bilgileri *id(INTEGER)*, *name VARCHAR(50)*, *birthday DATE*, *email VARCHAR(100)* olan bir tablo *oluşturalım.*

```
CREATE TABLE employee 
    (
	id SERIAL PRIMARY KEY,
	name VARCHAR(50) NOT NULL,
	birthday DATE NOT NULL,
	email VARCHAR(100) NOT NULL, 
	);
```

2. Oluşturduğumuz **employee** tablosuna **'Mockaroo'** servisini kullanarak *50* adet *veri ekleyelim.*

```
insert into employee (name, birthday, email) values ('Tarrah', '1991-03-15', 'tmowsdell0@posterous.com');
insert into employee (name, birthday, email) values ('Maddy', '2016-07-22', 'mwelfair1@icq.com');
insert into employee (name, birthday, email) values ('Wiley', '1974-05-24', 'wedkins2@cafepress.com');
insert into employee (name, birthday, email) values ('Reinhold', '2017-08-26', 'rcommucci3@blogger.com');
insert into employee (name, birthday, email) values ('Lorelei', '1972-12-21', 'laers4@sitemeter.com');
insert into employee (name, birthday, email) values ('Trixie', '1965-04-14', 'tmcmanus5@oaic.gov.au');
insert into employee (name, birthday, email) values ('Raye', '1977-05-16', 'rcorsar6@odnoklassniki.ru');
insert into employee (name, birthday, email) values ('Amalie', '1971-02-25', 'adelooze7@dell.com');
insert into employee (name, birthday, email) values ('Cody', '2011-07-16', 'crickesies8@oakley.com');
insert into employee (name, birthday, email) values ('Gale', '1978-03-04', 'gcornil9@marketwatch.com');
insert into employee (name, birthday, email) values ('Daisi', '1991-02-02', 'dbramera@blogtalkradio.com');
insert into employee (name, birthday, email) values ('Amandi', '2007-01-08', 'afullb@stanford.edu');
insert into employee (name, birthday, email) values ('Jimmy', '1965-02-03', 'jhasellc@xing.com');
insert into employee (name, birthday, email) values ('Joelle', '2016-12-14', 'jfried@cmu.edu');
insert into employee (name, birthday, email) values ('Julita', '1970-03-04', 'jmorforde@xing.com');
insert into employee (name, birthday, email) values ('Cirilo', '1977-04-21', 'ccameliaf@java.com');
insert into employee (name, birthday, email) values ('Ewan', '2007-06-25', 'eplesterg@yale.edu');
insert into employee (name, birthday, email) values ('Sullivan', '2020-11-17', 'sgulyh@ucsd.edu');
insert into employee (name, birthday, email) values ('Tobey', '1960-09-20', 'tmidghalli@zimbio.com');
insert into employee (name, birthday, email) values ('Fleur', '1961-10-17', 'fjelphsj@go.com');
insert into employee (name, birthday, email) values ('Sophi', '1990-11-12', 'sgummek@harvard.edu');
insert into employee (name, birthday, email) values ('Ansley', '1987-08-31', 'alenihanl@unblog.fr');
insert into employee (name, birthday, email) values ('Trent', '1967-05-17', 'tybarram@yandex.ru');
insert into employee (name, birthday, email) values ('Hunter', '2006-09-20', 'hkarolovskyn@furl.net');
insert into employee (name, birthday, email) values ('Michelle', '1984-03-05', 'myanuko@mysql.com');
insert into employee (name, birthday, email) values ('Shea', '1979-05-23', 'ssieurp@example.com');
insert into employee (name, birthday, email) values ('Kippy', '1972-09-11', 'kdunsmoreq@bizjournals.com');
insert into employee (name, birthday, email) values ('Cornelle', '2011-08-13', 'cmarquisr@youtube.com');
insert into employee (name, birthday, email) values ('Randall', '1983-10-09', 'rbartens@oaic.gov.au');
insert into employee (name, birthday, email) values ('Sidnee', '1985-12-26', 'scocklet@example.com');
insert into employee (name, birthday, email) values ('Jasper', '1967-05-22', 'jwellanu@sun.com');
insert into employee (name, birthday, email) values ('Sammy', '1977-07-14', 'sheathcotev@xrea.com');
insert into employee (name, birthday, email) values ('Fleurette', '1971-04-27', 'fbowskillw@mlb.com');
insert into employee (name, birthday, email) values ('Brittaney', '2022-07-17', 'bshivellx@msu.edu');
insert into employee (name, birthday, email) values ('Andrea', '1999-07-24', 'aabrashkovy@mtv.com');
insert into employee (name, birthday, email) values ('Una', '1986-07-27', 'ubrodyz@wsj.com');
insert into employee (name, birthday, email) values ('Kyle', '1983-02-15', 'kmoulster10@reuters.com');
insert into employee (name, birthday, email) values ('Irvine', '2005-12-31', 'ijirka11@sun.com');
insert into employee (name, birthday, email) values ('Garrek', '2006-03-01', 'gdoddrell12@sbwire.com');
insert into employee (name, birthday, email) values ('Sylvia', '1981-08-13', 'sruddlesden13@amazon.co.jp');
insert into employee (name, birthday, email) values ('Valenka', '1970-06-11', 'vroy14@cbc.ca');
insert into employee (name, birthday, email) values ('Zarah', '1989-03-14', 'zseak15@adobe.com');
insert into employee (name, birthday, email) values ('Artie', '1971-10-05', 'astubley16@storify.com');
insert into employee (name, birthday, email) values ('Reese', '1993-10-04', 'rdracey17@i2i.jp');
insert into employee (name, birthday, email) values ('Nona', '1984-06-28', 'noleksiak18@intel.com');
insert into employee (name, birthday, email) values ('Jeni', '1981-04-19', 'jcaldicot19@shareasale.com');
insert into employee (name, birthday, email) values ('Amby', '2017-08-14', 'alaurisch1a@un.org');
insert into employee (name, birthday, email) values ('Chiquia', '2020-12-03', 'cgilbey1b@desdev.cn');
insert into employee (name, birthday, email) values ('Vick', '2001-03-11', 'vhoneyghan1c@businessweek.com');
insert into employee (name, birthday, email) values ('Joline', '1975-05-23', 'jweeden1d@dedecms.com');

```

3. Sütunların **her birine** göre diğer sütunları güncelleyecek *5* adet **UPDATE** *işlemi yapalım.*

```
UPDATE employee
SET birthday = '2006-03-11'
WHERE id = '45';

UPDATE employee
SET name = 'jennifer'
WHERE birthday = '2011-07-16';

UPDATE employee
SET name = 'Amanda'
WHERE name = 'Joline';

UPDATE employee
SET name = 'Jasmine'
WHERE id = '4';

UPDATE employee
SET birthday = '2004-07-11'
WHERE email = 'ubrodyz@wsj.com';
```

4. Sütunların **her birine** göre ilgili satırı silecek *5* adet **DELETE** *işlemi yapalım.*

```
DELETE FROM employee
WHERE email = 'ssieurp@example.com';

DELETE FROM employee
WHERE name ='Randall';

DELETE FROM employee
WHERE birthday = '1990-11-12';

DELETE FROM employee
WHERE id >10
RETURNING *;

DELETE FROM employee
WHERE id = 23;
```