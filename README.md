# Temel-Elektronik-USB-Protokolu

Elektroniğin dijital dünyaya açılan kapısı: USB Protokolü

Bu ders notunda;

Temel Elektronik Dersi kapsamında USB (Universal Serial Bus) protokolünün yapısı, çalışma prensibi ve veri iletişim modları ele alınmıştır. 

USB’nin fiziksel pin yapısı, mimari katmanları, veri aktarım yöntemleri ve uygulama örnekleri üzerinden teorik ve pratik bir bakış sunulmuştur.

USB protokolünün temel prensipleri; pin bağlantıları, veri hattı (D+ / D−) iletişimi ve güç aktarımı açısından incelenmiştir. 

Mikrodenetleyici ve ortamında USB üzerinden veri haberleşmesi örneğiyle USB protokolün arduino nano prototatipleme kartı üzerinde pratik kullanımı ve kod örneği ele alınmıştır.

---

1. USB Nedir?

USB, bilgisayarlar ile çevre birimleri (fare, klavye, yazıcı, mikrodenetleyici kartları vb.) arasında veri ve güç aktarımını standartlaştıran seri iletişim protokolüdür.

Universal (Evrensel): Farklı cihazlarla uyumluluk sağlar.

Serial (Seri): Verileri bit bit aktarır.

Bus (Veri Yolu): Birden fazla cihazın aynı hat üzerinden haberleşmesine olanak tanır

---

2. USB Sürümleri

| Sürüm               | Yıl       | Maksimum Hız | Kablo Tipi / Not        |
| ------------------- | --------- | ------------ | ----------------------- |
| USB 1.0 / 1.1       | 1996      | 12 Mbps      | Düşük hız / Orta hız    |
| USB 2.0             | 2000      | 480 Mbps     | Yaygın kullanılan sürüm |
| USB 3.0 / 3.1 / 3.2 | 2008–2017 | 5–20 Gbps    | “SuperSpeed” mimarisi   |
| USB 4.0             | 2019      | 40 Gbps      | Thunderbolt 3 uyumlu    |

---

3. USB Fiziksel Katman (Pin Yapısı)

USB 2.0 Standart Kablo (Tip-A, Tip-B):     
| Pin | Renk    | Adı  | Açıklama       |
| --- | ------- | ---- | -------------- |
| 1   | Kırmızı | VBUS | +5V Güç Hattı  |
| 2   | Beyaz   | D−   | Veri (−) Hattı |
| 3   | Yeşil   | D+   | Veri (+) Hattı |
| 4   | Siyah   | GND  | Toprak         |

![alternatif metin](https://github.com/acetinkaya/Temel-Elektronik-USB-Protokolu/blob/main/usb20-1.png)

---

USB 3.0 kablolarda USB 2.0'a göre ek olarak 5 pin daha bulunur (SSTX±, SSRX±, GND_Drain).    
| Pin | Renk    | Adı  | Açıklama       |
| --- | ------- | ---- | -------------- |
| 1   | Kırmızı | VBUS | +5V Güç Hattı  |
| 2   | Beyaz   | D−   | Veri (−) Hattı |
| 3   | Yeşil   | D+   | Veri (+) Hattı |
| 4   | Siyah   | GND  | Toprak         |
| 5   | Mavi    | SSRX- | Hızlı Data Gönderici |
| 6   | Sarı    | SSRX+ | Hızlı Data Gönderici |
| 7   | Ground   | GND_Grain  |     Toprak     |
| 8   | Mor    | SSTX- |  Hızlı Data Alıcı     |
| 9   | Turuncu    | SSTX+ | Hızlı Data Alıcı  |
| Shell   | Konnektör Kabuğu  | Dış Folyo |  Plastik  |

![alternatif metin](https://github.com/acetinkaya/Temel-Elektronik-USB-Protokolu/blob/main/usb30-1.png)

---

4. USB Mimari Yapısı

USB iletişimi Host (Ana Cihaz) ve Device (Bağımlı Cihaz) arasında gerçekleşir. Veri alışverişi tek yönlüdür (host merkezlidir).

---> İletişim Akışı: Host → Hub → Device → Endpoint

Host Controller: PC veya mikrodenetleyici tarafı

Hub: Çoklayıcı (tek porttan çoklu cihaz bağlantısı)

Device: USB bellek, sensör, kamera vb.

Endpoint: Cihazın veri alışveriş noktaları (ör. IN/OUT uçları)

---

5. Veri Transfer Modları

| Mod                      | Özellik                      | Kullanım Alanı               |
| ------------------------ | ---------------------------- | ---------------------------- |
| **Control Transfer**     | Komutlar ve yapılandırmalar  | Cihaz tanımlama, enumeration |
| **Bulk Transfer**        | Büyük veri blokları          | USB bellek, yazıcı           |
| **Interrupt Transfer**   | Kesme tabanlı hızlı iletişim | Klavye, fare                 |
| **Isochronous Transfer** | Zaman hassasiyetli akış      | Ses, video veri akışı        |

---

6. USB Paket Yapısı

Bir USB veri çerçevesi (frame), paketlerden (packet) oluşur:

| SYNC | PID | ADDR | ENDP | CRC | DATA | EOP |

SYNC: Senkronizasyon başlatma
PID: Paket tipi tanımlayıcı
ADDR / ENDP: Hedef adres ve uç noktası
DATA: Veri alanı
EOP: Çerçeve sonu

---

7. Uygulama Örneği

--> Arduino üzerinde USB Protokolü ile Seri Haberleşme Uygulaması:

🧠 Bu örnekte, Arduino IDE programı üzerinden USB kablo aracılığıyla bilgisayara veri gönderimi yapılır. USB protokolü, aslında seri iletişimi (UART) sanal olarak USB portu üzerinden sağlar.

void setup() 
{
  Serial.begin(9600); // USB üzerinden seri haberleşme başlatılır 
}

void loop() 
{
  Serial.println("Merhaba Hayat");
  delay(1000);
}

---

8. Avantajlar ve Dezavantajlar

Avantajlar:

	Tak-çalıştır (Plug & Play) desteği
	Güç + veri aynı kablodan
	Geniş cihaz desteği
	Hızlı ve güvenilir iletişim

Dezavantajlar:

	Kablosuz alternatiflere göre mesafe sınırlıdır (5 m max).
	Host merkezli yapı, cihazlar arası doğrudan iletişime izin vermez.

---

9.  Görsel Şema 



DANIŞMANLI OGRENME @2025

Takip edip destek verdiğiniz için teşekkürler...

https://www.youtube.com/@danismanliogrenme

https://www.instagram.com/danismanliogrenme/




