# Normalizasyon Kuralları
### 1.Normalizasyon Kuralları
    1. Her tabloda bir kimlik kolonu olmak zorundadır.
    2. Bir kolonda birden fazla kayıt bulundurulmamalıdır.
    3. Her kolon sadece kendi bilgisinden sorumlu olmalıdır. 
### 2.Normalizasyon Kuralları
    1. Birinci normalizasyon kurallarının uygulanması.
    2. Yatay tekrar söz konusu olamaz. Örneğin oyuncu1, oyuncu2 gibi kolonlar olamaz. Onun yerine farklı bir tabloda kayıt yapabiliriz.
    3. Tekrar eden kolonladı veriler farklı tablolar ile ayrıştırılmalıdır. Bire çok ilişki örneğidir. (ForeignKey Mantığı)
### 3.Normalizasyon Kuralları
    1. İkinci normalizasyon kuralları geçerlidir.
    2. Çoka çok ilişkinin uygulanması gerekir.