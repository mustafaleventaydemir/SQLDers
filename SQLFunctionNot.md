# String Fonksiyonlar
1. ASCII() Fonksiyonu
```sql
select ASCII(ContactName) AS ContNameAscii, ContactName
from Customers --ContactName'in baş harfine bakar ve ASCII değerini bize döner.
```
2. CHAR() Fonksiyonu
```sql
select char(65) --char fonksiyonunda harfler 65 ASCII değeriyle başlar ve alfabetik ilerler.
--65 bize A harfini döndürür.
```
3. CHARINDEX()
```sql
select charindex('v', 'Levent') --verilen harfin index numarasını bize geri döner. Eğer verilen harf kelimenin içerisinde yoksa 0 dönecektir.
select charindex('v', 'Levent', 3) --buradaki 3 değeri bize aramaya 3. indexten başla anlamındadır. Gerekli yerlerde kullanılabilir.
```
4. CONCAT() Fonksiyonu
```sql
select concat('Mustafa', ' Levent', ' Aydemir')--iki veya daha fazla string değeri birleştirir.
```
5. CONCAT_WS() Fonksiyonu
```sql
select concat_ws('.','www','leventaydemir','com') --verilen ilk parametre diğer verilen parametrelerin arasına gelir. örneğin çıktısı -->www.leventaydemir.com 
```
6. DATALENGTH() Fonksiyonu
```sql
select datalength(' leventaydemir ') --verilen değerin toplam harf sayısını geri döndürür.
--NOT: değerin başında ve sonundaki boşluklar dahil edilir.
```
7. DIFFERENCE() Fonksiyonu
```sql
select difference('levent', 'aydemir') --verilen iki değer arasındaki benzerliğe bakar ve 0-4 arasında değer döner.
```
8. FORMAT() Fonksiyonu
```sql
select format(24021997, '##-##-####') --verilen sayısal veriyi belirtilen şekilde geri döner. örneğin çıktısı -->24-02-1997 şeklindedir.
```
9.  LEFT() - RIGHT() Fonksiyonu
```sql
select left(ContactName, 6)
from Customers --ContactName'in soldan başlayarak 6 harfini döndürür.
select right(ContactName, 6)
from Customers --ContactName'in sağdan başlayarak 6 harfini döndürür.
```
10. LEN() Fonksiyonu
```sql
select len(' leventaydemir     ')--verilen değerin harf sayısını döner. datalength'ten farkı sondaki boşlukları saymaz ama baştaki boşlukları sayar.
```
11. LOWER() - UPPER() Fonksiyonu
```sql
select lower('LeveNt AYDEMir')--verilen değeri küçük harfe çevirir.
select upper(ContactName)
from Customers--verilen değeri büyük harfe çevirir.
```
12. LTRIM() - RTRIM() Fonksiyonu
```sql
select ltrim('     leventaydemir') --soldan boşlukları siler.
select rtrim('leventaydemir     ') --sağdan boşlukları siler.
```
13. NCHAR() Fonksiyonu
```sql
select nchar(65) --verilen değerin Unicode karakterini geri döndürür.
```
14.PATINDEX() Fonksiyonu
```sql
select patindex('%e%','Levent')--harf karşılatırması yapar ve hangi indexte olduğunu döner.
select patindex('%[nt]%','Levent') --aynı şekilde hangi indexte olduğunu döner.
```
15. QUOTENAME() Fonksiyonu
```sql
select quotename('leventaydemir') --verilen değeri köşeli parantez içerisinde bize geri döner.
select quotename('leventaydemir','{}') -- {}, <>, "", () belirterek bunların içerisinde değeri döndürebiliriz.
```
16. REPLACE() Fonksiyonu
```sql
select replace('Levent Aydemir','e','a') --verilen değer içerisindeki e harflerini a harfi ile değiştirip bize döner.
select replace('Levent Aydemir','Levent','Mustafa') --Kelimede değiştirebiliriz.
--NOT: Değişen değer büyük küçük harfe duyarlıdır.
```
17. REPLICATE() Fonksiyonu
```sql
select replicate('levent aydemir',3) --belirtilen değeri verilen sayı kadar tekrarlar ve geri döndürür.
select replicate(ContactName,3)
from Customers
```
18. REVERSE() Fonksiyonu
```sql
select reverse('levent aydemir') --verilen değeri tersten yazdırır.
```
19. SPACE() Fonksiyonu
```sql
select space(10) --10 boşluklu bir değer döndürür.
```
20. STR() Fonksiyonu
```sql
select str(10.5555,6,2) --numerik bir veriyi stringe çevirir.
-- ilk parametre sayı, ikincisi kaç haneli istediğimiz, üçüncüsü ise virgülsen sonra kaç hane olsun şeklindedir.
```
21. STUFF() Fonksiyonu
```sql
select stuff('levent aydemir', 1, 6, 'mustafa')--girilen değerin 1. karakterinden başlayıp 6 karakter sil. ve yerine mustafa yaz anlamı taşır.
--replace fonksiyonuna benzer.
select stuff('levent aydemir!', 15, 1, 'mustafa') --15. karakterden başla ve 1 karakter sil. yerime mustafa yaz anlamındadır.
```
22. SUBSTRING() Fonksiyonu
```sql
select substring('levent aydemir', 1, 6) --1. karakterden başla ve 6'ya kadar olan değeri döndür. sonuç levent çıkacak.
```
23. TRANSLATE() Fonksiyonu
```sql
select translate('3*[2+4]/{4-3}', '[]{}','()()') -- []{} içerisinde olanları ()() içerisine al ve geri döndür.
```
24. TRIM() Fonksiyonu
```sql
select trim('    levent    ') --sağdan ve soldan tüm boşlukları siler.
```
25. UNICODE() Fonksiyonu
```sql
select unicode('levent')--verilen değerin ilk harfinin Unicode değerini döner.
```
# Numeric Fonksiyonlar
1. ABS() Fonksiyonu
```sql
select abs(-152.2) -- verilen değerin mutlak değerini döndürür.
```
2. ACOS() Fonksiyonu
```sql
select acos(0.25) --verilen değerin arkcosinüsünü döndürür.
```
3. ASIN() Fonksiyonu
```sql
select asin(0.25) --arksinüs döndürür
```
4. ATAN() Fonksiyonu
```sql
select atan(2.5) --arktanjant döndürür
```
5. ATN2() Fonksiyonu
```sql
select atn2(0.50 , 1) --arktanjant döndürür.
```
6. AVG() Fonksiyonu
```sql
select avg(UnitPrice) from Products --değerlerin ortalamarını hesaplar.
```
7. CEILING() Fonksiyonu
```sql
select ceiling(36.70) --ondalıklı sayıyı bir üste yuvarlar.
```
8. COUNT() Fonksiyonu
```sql
select count(ProductID) from Products --Belirtilen sütunun kaç tane kaydı var bize döndürür.
```
9. COS() Fonksiyonu
```sql
select cos(2) --değerin kosinüsünü döndürür.
```
10. COT() Fonksiyonu
```sql
select cot(6) --değerin kotanjantını döndürür
```
11. SIN() Fonksiyonu
```sql
select sin(2) --sayının sinüsünü döndürür.
```
12. TAN() Fonksiyonu
```sql
select tan(1.75) --sayının tanjantını döndürür.
```
13. DEGREES() Fonksiyonu
```sql
select degrees(1.5) --radyan cinsinden değeri dereceye döndürür.
```
14. FLOOR() Fonksiyonu
```sql
select floor(25.75) --ondalıklı sayı bir alta yuvarlar.
```
15. LOG() Fonksiyonu
```sql
select log(2) --değerin logaritmasını döndürür.
```
16. LOG10() Fonksiyonu
```sql
select log10(2) --değerin 10'luk tabandaki logaritmasını döndürür.
```
17. MAX() Fonksyionu
```sql
select max(UnitPrice) from Products --en yüksek kaydı getirir.
```
18. MIN() Fonksiyonu
```sql
select min(UnitPrice) from Products --en düşük kaydı getirir.
```
19. PI() Fonksiyonu
```sql
select pi() --pi değerini döndürür.
```
20. POWER() Fonksiyonu
```sql
select power(4,2) --4'ün 2. üssünü alır 
```
21. RADIANS() Fonksiyonu
```sql
select radians(180) --dereceyi radyan değere döndürür.
```
22. RAND() Fonksiyonu
```sql
select rand() --0-1 arasında rastgele sayı döndürür.
```
23. ROUND() Fonksiyonu
```sql
select round(234.423, 2) -- sayının odalığının son iki basamağını yukarı ya da aşağı yuvarlar.
```
24. SIGN() Fonksiyonu
```sql
select sign(255.5) --sayı 0'dan büyükse 1 dönecek.
--0'dan küçükse -1
--0'a eşitse 0 dönecek
```
25. SQRT() Fonksiyonu
```sql
select sqrt(64) --sayının karekökünü döner.
```
26. SQUARE() Fonksiyonu
```sql
select square(64) --sayının karesini döner
```
27. SUM() Fonksiyonu
```sql
select sum(Quantity) from OrderDetails --Quantity'nin toplamını döndürür.
```