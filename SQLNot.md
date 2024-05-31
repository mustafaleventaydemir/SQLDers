## En çok kullanılan sql komutları
1. SELECT
    1. Veri tabanından verileri çıkarır.
2. UPDATE
    1. Veritabanındaki verileri günceller.
3. DELETE
    1. Veritabanındaki verileri siler.
4. INSERT INTO 
    1. Veritabanına yeni veri ekler.
5. CREATE DATABASE
    1. Yeni veritabanı oluşturur.
6. ALTER DATABASE
    1. Veritabanını değiştirir.
7. CREATE TABLE
    1. Veritabanına yeni tablo ekler.
8. ALTER TABLE
    1. Veritabanındaki tabloyu değiştirir.
9. DROP TABLE
    1. Veritabanındaki tabloyu siler.
10. CREATE INDEX 
    1. 
11. DROP INDEX

 
```sql 
--SELECT Veritabanındaki kayıtları getirmemizi sağlar.

select * from Customers --Customers tablosundaki tüm verileri getirir
select CustomerName, City from Customers --Customers tablosundaki CustomerName ve City sütunlarındaki verileri getirir
select distinct Country from Customers --select distinct aynı değerleri tek olarak bize getirir
select count (distinct Country) from Customers --Customers tablosunda kaç tane ülke olduğunu sayı olarak getirir
```
```sql
--WHERE sorgularımıza bir koşul oluşturur. Ayrıca Update, Delete gibi sorgularda da kullanılır.

select * from Customers Where City="London" --Customers tablosunda şehiri London olan kayıtları getirir.
select * from Employees Where EmployeeID>3 --Employees tablosunda EmployeeID'si 3'ten büyük olanları getirir. =, >, <, >=, <=, <>(!=) diğer kullanılan operatörlerdendir.
select * from Employees Where EmployeeID Between 2 and 5 --EmployeeID'si 2 ile 5 arasında olan verileri getirir.
select * from Employees Where City like 's%'--City ismi s ile başlayan verileri getir. (%d dersek eğer City isminin son harfi d olanları getirir.)
select * from Employees where LastName in ('Fuller','King') --Lastname'i Fuller ve King olanları getirir.

```
```sql
--ORDER BY istenilen verileri artan veya azalan şekilde sıralamamızı sağlar.
select * from Products order by UnitPrice --Default olarak Products tablosu UnitPrice'a göre küçükten büyüğe sıralandı.
select * from Products order by UnitPrice asc --asc yine küçükten büyüğe sıralar
select * from Products order by UnitPrice desc--desc ise büyükten küçüğe sıralar. Aynı zamanda verileri alfabetik olarakta sıralayabiliriz.
select * from customers order by Country, ContactName --ilk ülkeye göre sıralar ve aynı ülkelerden olan verileri ise ContactName'e göre sıralar.
select * from customers order by Country asc, ContactName desc --Ülkeyi alfabetik artan sıraya göre, contactName'i alfabetik azalan sıraya göre sıralar.
```
```sql
--AND operatörü birden fazla koşulu 've' anlamında bağlar
select * from customers where city="Berlin" and region="Western Europe" --city=berlin ve region=Western Europe olan verileri getirir.
select * from customers where Country="Germany" and city="Berlin" and region="Western Europe"--birden fazla AND operatörü kullanabiliriz.

--OR operatörü birden fazla koşulu 'veya' anlamında bağlar
select * from customers where city="Berlin" or region="Western Europe" --city=Berlin veya region=Western Europe olanları getirir.
select * from customers where Country="Germany" or city="Berlin" or region like 'W%' --birden fazla OR operatörü kullanabiliriz.

--AND - OR ÖRNEĞİ
--customers tablosunda ülkesi Almanya olan VE firma adı B VEYA D ile başlayan verileri getir
SELECT * from customers where Country="Germany" and (CompanyName like 'B%' or CompanyName like 'D%')
--NOT: like koşulunu parantez içerisine almasaydık ülkesi Almanya ve firma adı baş harfi B olan veya firma adı baş harfi D olan verileri getirir.
```
```sql
--NOT operatörü .... olmayan verileri getirir.
select * from customers where not Country="Germany" --customers tablosunda ülkesi Almanya olmayanları getirdi.
select * from customers where CompanyName not like 'C%' --CompanyName'i C harfi ile başlamayan verileri getirdi.
select * from Categories where CategoryID not between 2 and 4 --categoryID'si 2 ve 4 arasında olmayan verileri getirdi.
select * from customers where city not in ('Berlin', 'London') --şehiri Berlin ve London olmayan verileri getirir. Böylece birden fazla olmaması gereken şartları verebiliriz.
select * from Categories where not CategoryID>2--CategoryID'si 2'den büyük olmayan verileri getirir.
```
```sql
--INSERT INTO Tabloya yeni bir veri eklemek için kullanılır.
--tablo ismi ve kolon isimlerini vererek ekleyebiliriz.
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...)
--Tablolara iki şekilde ekleme yapılabilir.
--Tablo ismini verip kolon isimlerini vermeden ama tablodaki kolonlara uygun şekilde yazarak ekleyebiliriz
INSERT INTO table_name
VALUES (value1, value2, value3, ...)
--ÖRNEK
insert into Customers (CompanyName, ContactName, ContactTitle,City, Country) 
values ('ABC Şirketi','Mustafa Levent Aydemir','Software Developer','Kastamonu','Türkiye') --Customers tablosundaki bütün kolonlarada ekleme yapabiliriz ya da belirttiğimiz kolonlarada ekleme yapabiliriz.
insert into Customers (CompanyName, ContactName, ContactTitle,City, Country) 
values ('AAC Şirketi','Mustafa Levent Aydemir','Software Developer','Kastamonu','Türkiye'),
('ACC Şirketi','Muhammed Emre Nefesli','Software Developer','Yozgat','Türkiye'),
('ADC Şirketi','Gökhan Pirizoğlu','F-16 Makinist','Kastamonu','Türkiye')
--birden çok ekleme yapmak bu şekilde mümkündür.
```
```sql
-- IS NULL ve IS NOT NULL
select * from customers where Address is null--Customers tablosunda Adress sütunu null olan kayıtları getirir.
select * from customers where Address is not null--Customers tablosunda Adress sütunu null olmayan kayıtları getirir.
```
```sql
--UPDATE ..... SET tablo sütunları güncelleme
update customers set Address="Hocaimat Mahallesi"
where ContactName='Mustafa Levent Aydemir' --customers tablosunda contactName'i Mustafa Levent Aydemir olan kaydın Address'i Hocaimat Mahallesi olarak güncellendi
update customers set Address="Hocaimat Mahallesi", PostalCode='37300'
where ContactName='Mustafa Levent Aydemir' --Bu şekilde iki ayrı kolonu güncelleyebiliriz.
update customers set ContactName='Juan'
where Country='Mexico' --Ülkesi Meksika olan tüm kayıtların contactName'i Juan olarak güncellendi.
--!ÖNEMLİ!
--Where koşulunu yazmazsak tüm tabloda güncelleme yapar ve sıkıntı çıkar.
```
```sql
--DELETE tablodaki kayıtları silmek için kullanılır.
delete from customers where ContactName='Levent'--customers tablosunda ContactName'i Levent olan kaydı siler.
delete from Customers --Customers tablosu içerisindeki tüm kayıtları siler
drop table Customers --Customers tablosunu tamamen siler.
--!ÖNEMLİ!
--Foreign key ile bağlı olan kayıtlarda silme işlemi direkt yapılamaz. ON DELETE CASCADE kullanımıyla bu sorunu ileride çözeceğiz.
```
```sql
--SELECT TOP listelenecek kayıt sayısını belirlemek için kullanılır.
select * from customers limit 4 --customers tablosunun ilk 4 kaydını getirir.
select * from customers where CompanyName like 'B%' limit 3 --CompanyName baş harfi B olan ilk 3 kaydı getirir.
select * from customers order by ContactName desc limit 3--sıralama işlemi yapıp belirli sayıda kayıt getirilebilir.
--!ÖNEMLİ!
--Her veritabanı sistemi aynı kodu desteklemez.
--SQL Server/MS Access
SELECT TOP sayı|yüzde(percent) column_name(s)
FROM table_name
WHERE condition; 
--MySQL
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
--Oracle 12
SELECT column_name(s)
FROM table_name
ORDER BY column_name(s)
FETCH FIRST number ROWS ONLY;
--Older Oracle
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```
```sql
--Aggregate İşlemleri
--MIN VE MAX minimum ve maksimum değerleri getirir
select min(UnitPrice)
from Products--fiyatı en düşük olan kaydı getirir.
select max(UnitPrice)
from Products--fiyatı en yüksek olan kaydı getirir.
--!ÖNEMLİ!
select max(UnitPrice) AS Fiyat
from Products--AS kullanarak UnitPrice sütununa Fiyat takma ismini verdik.
select min(UnitPrice) AS Fiyat, CategoryID
from Products
group by CategoryID--group by ile her kategorideki en düşük fiyat kayıtlarını getirdi.
--GROUP BY ilerleyen kısımlarda daha detaylı anlatılacak.

--COUNT belirtilen şartlarda varolan kayıt sayısını gösterir.
select count(*)
from Products--Products tablosundaki kayıt sayısını(satır sayıları) verir.
select count(ProductName)
from Products--(*) yerine sütun adı verirsek null olmayan kayıtları bize getirir.
select count(ProductID)
from Products
where UnitPrice>20--Fiyatı 20'den yüksek olan kayıtların sayısını verir.
select count(DISTINCT UnitPrice)
from Products
where UnitPrice>18--DISTINCT kullanarak fiyatı aynı olanları sadece bir kere saydı ve değerini bize verdi.
select count(*) AS [Kayıt Sayısı]
from Products--AS[**** *****] şeklinde sütun ismini değiştirip çıktıyı alabiliriz.
select count(*) AS [Kayıt Sayısı], CategoryID AS KategoriID
from Products
group by CategoryID --CategoryID'ye göre gruplandırıldığında CategoryID'ye göre kaçar tane kayıt varsa bize getirir.

--SUM belirtilen şartlardaki kayıtların toplamını bize verir.
select SUM(Quantity)
From OrderDetails --OrderDetails tablosundaki Quantity sütunu kayıtlarının toplamını verir.
select SUM(Quantity) AS Toplam
From OrderDetails
where ProductID=11 --belirtilen şarta göre kayıtların toplamını verir.
select OrderID, SUM(Quantity) AS [Toplam Miktar]
from OrderDetails
Group By OrderID --OrderID'ye göre gruplandırıp toplam miktarları verir.
SELECT SUM(Price * Quantity)
FROM OrderDetails
LEFT JOIN Products ON OrderDetails.ProductID = Products.ProductID--OrderDetails'i Products ile birleştirip toplam tutarı buluruz. 
--JOIN'leri ilerleyen kısımlarda detaylandıracağız.

--AVG Sayısal sütunların ortalamalarını hesaplar
select avg(UnitPrice)
from Products --Products Tablosundaki UnitPrice'ın ortalamasını verir.
select avg(UnitPrice) AS [Ortalama Birim Fiyatı]
from Products
where CategoryID=2 --CategoryID'si 2 olanların ortalamasını verir.
select * from Products
where UnitPrice > (select avg(UnitPrice) from Products) --Ortalama birim fiyatın üzerindeki kayıtları getirir. !Güzel bir örnek tekrar et.
select avg(UnitPrice) AS BirimFiyat, CategoryID
from Products
group by CategoryID --CategoryID'ye göre gruplandırılan kayıtların ortalama BirimFiyatlarını bize getirir.

--LIKE belirli kelime ya da harfe göre arama yapma işlemlerinde kullanılır.
select * from Customers
where ContactName like 'a%' --a harfi ile başlayan ContactName'leri getirir.
select * from Customers
where ContactName like '%a' --a harfi ile biten kayıtları getirir.
select * from Customers
where city like '%L%' --içerisinde L harfi bulunan kayıtları getirir.
select * from Customers
where ContactName like 'La%' --La ile başlayan müşteri kayıtlarını getirir.
select * from Customers
where city like 'L_nd__' --L ile başlayan ardından wildcard(joker karakter) olan ve nd ile devam edip iki tane joker karakter olan tüm kayıtları getirir.
select * from Customers
where ContactName like 'a%' or ContactName like 'b%'
order by ContactName --a veya b ile başlayan kayıtları getirip contactName'e göre alfabetik sıralar.
select * from Customers
where ContactName like 'e%n' --e ile başlayıp n ile biten kayıtları getirir.
select * from Customers
where ContactName like 'a__%' --a ile başlayan ve en az 3 karakter olan kayıtları getirir.
select * from Customers
where ContactName like '_u%' --ikinci harfi r olan kayıtları getirir.
select * from Customers
where Country like 'Spain' --herhangi bir joker karakter belirtilmemişse like içine yazılan ifadenin tablodaki ifadeyle birebir olması gerekir.
```
```sql
-- IN Operatörü birden fazla OR operatörünün kısaltmasıdır.
select * from Customers 
where Country IN('Germany','France','Brazil') --Ülkesi Almanya, Fransa veya Brezilya olan tüm kayıtları getir.
select * from Customers 
where Country NOT IN('Germany','France','Brazil')--Ülkesi Almanya, Fransa veya Brezilya olmayan tüm kayıtları getir.
select * from Customers 
where CustomerID IN (select CustomerID from Orders) --Orders tablosunda siparişi olan tüm müşteri kayıtlarını getirir.
select * from Customers 
where CustomerID NOT IN (select CustomerID from Orders) --Orders tablosunda siparişi olmayan tüm müşteri kayıtlarını getirir.
```
```sql
-- BETWEEN Operatörü belirli değerler arasındaki kayıtları getirmemizi sağlar
select * from Products
Where UnitPrice BETWEEN 10 AND 20 --Birim fiyatı 10-20 arasında olan kayıtları getirir.
select * from Products
Where UnitPrice NOT BETWEEN 10 AND 20 --Birim fiyatı 10-20 arasında olmayan kayıtları getirir.
select * from Products
Where UnitPrice BETWEEN 10 AND 20 and CategoryID IN (1,2,3) --Birim fiyatı 10-20 arasında olan ve CategoryID'si 1,2,3 olan kayıtları getirir.
select * from Products
where ProductName BETWEEN 'Carnarvon Rigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName --Belirtilen ProductName'ler arasındaki tüm kayıtları ProductName'in alfabetik sırasına göre getirir.
select * from Products
where ProductName NOT BETWEEN 'Carnarvon Rigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName --Belirtilen ProductName'ler arasında olmayan tüm kayıtları ProductName'in alfabetik sırasına göre getirir.
select * from Orders
Where OrderDate BETWEEN '2016-05-01' AND '2016-07-04' --Tarihler arasındaki sipariş kayıtlarını getirir.
```
```sql
--Aliases (AS) Takma Ad
select CustomerID AS ID
From Customers --CustomerID'ye ID takma adını verdik.
select CustomerID ID
From Customers --AS kullanmadan bu şekilde de takma ad verilebilir. Kullanılması tercih edilir.
select ProductName AS [En İyi Ürünler]
from Products --Boşluk içeren takma adlar vermek için çift tırnak içinde ya da köşeli parantez içinde kullanıyoruz.
SELECT ContactName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers --4 tane sütunu birleştirip tek bir takma ad verilebilir.
SELECT * FROM Customers AS Persons --Tablolarımızada takma ad verebiliriz.
SELECT o.OrderID, o.OrderDate, c.ContactName
FROM Customers AS c, Orders AS o
WHERE c.ContactName='Around the Horn' AND c.CustomerID=o.CustomerID --tablolara takma isim vererek yazmış olduğumuz kodları kısaltabilir ve anlaşılabilirliğini artırabiliriz.
```
```sql
--***JOIN*** iki veya daha fazka tablodaki satırları, aralarındaki ilgili sütuna göre birleştirir.
select o.OrderID, c.ContactName, o.OrderDate
from Orders AS o
INNER JOIN Customers AS c ON o.CustomerID=c.CustomerID --Orders tablosu ile Customers tablosunun aralarında bağlantı olan CustomerId'lerin birbirine eşit olanlarının kayıtlarını getirir.
SELECT o.OrderID, c.ContactName, s.CompanyName
FROM ((Orders AS o 
INNER JOIN Customers AS c ON o.CustomerID=c.CustomerID)
INNER JOIN Shippers AS s ON o.ShipVia=s.ShipperID) --3 tablonun birbiriyle bağlantılı olan ortak kayıtlarını getirir.
--**LEFT JOIN**
SELECT c.ContactName,o.OrderID
FROM Customers AS c 
LEFT JOIN Orders AS o ON c.CustomerID=o.CustomerID
ORDER BY c.ContactName -- Customers(sol) tablodaki tüm kayıtlar gelir ve Orders(sağ) tablosundaki CustomerID'leri eşleşen kayıtlar gelir.
--**RIGHT JOIN
SELECT o.OrderID, e.LastName, e.FirstName
FROM Orders AS o 
RIGHT JOIN Employees AS e ON o.EmployeeID=e.EmployeeID --Employees(sağ) tablosundaki tüm kayıtlar gelir ve Orders(sol) tablosundaki EmployeeID'leri eşleşen kayıtlar gelir.
SELECT c.ContactName, o.OrderID
FROM Customers AS c
FULL OUTER JOIN Orders AS o ON c.CustomerID=o.CustomerID
ORDER BY c.ContactName --Customers ve Orders tablosundaki tüm kayıtlar gelir. Kayıtlar eşleşsede eşleşmesede kayıtlar getirilir.
--**SELF JOIN Bir tabloyu kendisiyle birleştirme işlemlerinde kullanılır.
SELECT a.ContactName AS ContactName1, b.ContactName AS ContactName2, a.City, a.CustomerID, b.CustomerID
FROM Customers AS a, Customers AS b
WHERE a.CustomerID <> b.CustomerID
AND a.City=b.City
ORDER BY a.City --2 ayrı Customers tablosunda CustomerID'leri birbiriyle aynı olmayan ve City'leri birbiriyle aynı olan kayıtları City'lerine göre alfabetik sırayla getirir.
--!ÖNEMLİ
--Bazı veritabanlarında LEFT JOIN ya da RIGHT JOIN, LEFT OUTER JOIN ve RIGHT JOIN olarak adlandırılır.
--**RIGHT JOIN**


```
![C:\Users\musta\OneDrive\Masaüstü\SQLDers](img_inner_join.png)
![C:\Users\musta\OneDrive\Masaüstü\SQLDers](img_left_join.png) 
![C:\Users\musta\OneDrive\Masaüstü\SQLDers](img_right_join.png) 
![C:\Users\musta\OneDrive\Masaüstü\SQLDers](img_full_outer_join.png) 
```sql
--**UNION Birdeb fazla Select ifadesinin sonucunu tek bir sütunda toplar ve getirir.
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
UNION
SELECT City FROM Employees
ORDER BY City --Customers, Suppliers ve Employees tablolarından City kayıtlarını aldı ve hepsini birleştirerek tek sütunda bize getirdi.
SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers --UNION ALL dersek birleştirmeden kaçar tane varsa o şekilde bize geri getirir.
SELECT City FROM Customers
WHERE Country="Germany"
UNION
SELECT City FROM Suppliers
WHERE Country="Germany"
ORDER BY City --Sadece ülkesi Almanya olan değerler getirilir.
SELECT City FROM Customers
WHERE Country="Germany"
UNION ALL
SELECT City FROM Suppliers
WHERE Country="Germany"
ORDER BY City --Sadece ülkesi Almanya olan değerler getirilir ve UNION ALL olduğu için yinelenen kayıtlarda getirilir.
SELECT 'Customer' AS Type,ContactName, City, Country
FROM Customers
UNION
select 'Supplier',ContactName, City, Country
FROM Suppliers --Tüm Customers ve Suppliers'leri getirir. Gelen kayıtların nereden geldiğini anlamak için geçici bir tip oluşturduk. Ve buna takma ad verdik.
```
```sql
--**GROUP BY aynı değerlere ait olan kayıtları tek kayıt olarak almamıza sağlar.
SELECT count(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY count(customerID) DESC --Customers tablosunda ülkeleri gruplandırarak CustomerID sayılarına göre getiriyor. ve en son yine CustomerID sayılarına göre büyükten küçüğe sıralıyor.
SELECT s.CompanyName, count(o.OrderID) AS NumberOfOrders FROM Orders AS o
LEFT JOIN Shippers AS s ON o.ShipVia=s.ShipperID
GROUP BY CompanyName --Orders(sol) tablosundaki tüm verileri ve Orders'ın içinde bulunan Shipper tablosundaki kayıtlarını CompanyName'e göre gruplandırıp OrderID değerlerini getirir.
```
```sql
--**HAVING
```
