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
select rtrim('     leventaydemir') --sağdan boşlukları siler.
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
