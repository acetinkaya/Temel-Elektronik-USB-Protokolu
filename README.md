# Temel-Elektronik-USB-Protokolu

Elektroniğin dijital dünyaya açılan kapısı: USB Protokolü

Bu ders notunda;

Temel Elektronik Dersi kapsamında USB (Universal Serial Bus) protokolünün yapısı, çalışma prensibi ve veri iletişim modları ele alınmıştır. 

USB’nin fiziksel pin yapısı, mimari katmanları, veri aktarım yöntemleri ve uygulama örnekleri üzerinden teorik ve pratik bir bakış sunulmuştur.

USB protokolünün temel prensipleri; pin bağlantıları, veri hattı (D+ / D−) iletişimi ve güç aktarımı açısından incelenmiştir. 

Mikrodenetleyici ve ortamında USB üzerinden veri haberleşmesi örneğiyle USB protokolün arduino nano prototatipleme kartı üzerinde pratik kullanımı ve kod örneği ele alınmıştır.

---

USB Nedir?

USB, bilgisayarlar ile çevre birimleri (fare, klavye, yazıcı, mikrodenetleyici kartları vb.) arasında veri ve güç aktarımını standartlaştıran seri iletişim protokolüdür.

Universal (Evrensel): Farklı cihazlarla uyumluluk sağlar.

Serial (Seri): Verileri bit bit aktarır.

Bus (Veri Yolu): Birden fazla cihazın aynı hat üzerinden haberleşmesine olanak tanır

---

USB Sürümleri

| Sürüm               | Yıl       | Maksimum Hız | Kablo Tipi / Not        |
| ------------------- | --------- | ------------ | ----------------------- |
| USB 1.0 / 1.1       | 1996      | 12 Mbps      | Düşük hız / Orta hız    |
| USB 2.0             | 2000      | 480 Mbps     | Yaygın kullanılan sürüm |
| USB 3.0 / 3.1 / 3.2 | 2008–2017 | 5–20 Gbps    | “SuperSpeed” mimarisi   |
| USB 4.0             | 2019      | 40 Gbps      | Thunderbolt 3 uyumlu    |

---

USB Fiziksel Katman (Pin Yapısı)

USB 2.0 Standart Kablo (Tip-A, Tip-B):
| Pin | Renk    | Adı  | Açıklama       |

