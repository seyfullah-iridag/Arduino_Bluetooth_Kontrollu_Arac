# 🚗 Arduino Bluetooth Kontrollü Araç

Bu proje, seri port (Bluetooth/USB) üzerinden gönderilen karakter
komutları ile iki adet DC motoru kontrol eden bir Arduino uygulamasıdır.

------------------------------------------------------------------------

## 📌 Proje Özeti

-   Seri haberleşme ile kontrol\
-   PWM ile hız ayarı\
-   İleri / geri / sağ / sol hareket\
-   Dur komutu\
-   Çift motor kontrolü\
-   Güvenli sabit tanımlama (`const int`)

------------------------------------------------------------------------

## 🛠 Kullanılan Donanımlar

-   Arduino (Uno / Nano vb.)
-   Bluetooth Modül (HC-05 / HC-06)
-   L298N veya L293D motor sürücü
-   2 adet DC motor
-   Harici güç kaynağı
-   Robot araba platformu

------------------------------------------------------------------------

## 🔌 Pin Tanımlamaları

``` cpp
const int sag_enable = 11;  
const int sag_ileri = 10;   
const int sag_geri = 9;     

const int sol_ileri = 8;    
const int sol_geri = 7;     
const int sol_enable = 6;   
```

  Pin   Görev
  ----- ------------------------
  11    Sağ Motor Enable (PWM)
  10    Sağ Motor İleri
  9     Sağ Motor Geri
  8     Sol Motor İleri
  7     Sol Motor Geri
  6     Sol Motor Enable (PWM)

------------------------------------------------------------------------

## 🎮 Kontrol Komutları

  Komut   Açıklama
  ------- -----------
  `F`     İleri Git
  `B`     Geri Git
  `R`     Sağa Dön
  `L`     Sola Dön
  `S`     Dur

------------------------------------------------------------------------

## ⚙️ Çalışma Mantığı

1.  Seri porttan karakter okunur.\
2.  Gelen karakter kontrol edilir.\
3.  Motor yön pinleri ayarlanır.\
4.  Enable pinine PWM uygulanır.\
5.  Araç ilgili hareketi yapar.

------------------------------------------------------------------------

## 🔎 Neden `#define` Değil `const int`?

Bu projede sabit tanımlamalar için `#define` yerine `const int` tercih
edilmiştir.

### Avantajları:

-   Veri tipi vardır (type safety)
-   Debug sırasında görülebilir
-   Modern C++ standartlarına uygundur
-   Daha okunabilir kod yapısı sağlar

------------------------------------------------------------------------

## 🔧 PWM Hız Kontrolü

``` cpp
analogWrite(sag_enable, 255);
```

PWM aralığı:

-   0 → Durur\
-   255 → Maksimum hız

------------------------------------------------------------------------

## 👤 Hazırlayan

**Seyfullah İridağ**\
2026
