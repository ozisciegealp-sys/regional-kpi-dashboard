# Bölge KPI Kontrol Platformu

Çok mağazalı bir bölgenin satış, kârlılık, CRM, paket servis, ürün karması, fire, envanter, eğitim, personel devri, misafir şikâyeti ve denetim göstergelerini **tek tabloda**, hedefe göre renklendirilmiş olarak gösteren ve her mağazaya **100 üzerinden performans puanı** veren Excel platformu.

> **Not:** Bu dosya, bir kahve zincirinde 16 mağazalık bölge için kurduğum ve her ay yürüttüğüm platformun **sahte veriyle yeniden kurulmuş sürümüdür**. Orijinali şirketin SharePoint ortamında çalışıyordu. Yapı (kaynak sayfalar, genel tablo, hedef satırı, dönem seçimi, performans puanı) orijinalden alınmıştır. Mağaza adları, rakamlar ve açıklamalar uydurmadır.
>
> Performans puanındaki **katsayılar örnek değerdir**; orijinal sistemde her kalemin kendi katsayısı vardı. Hedef değerleri orijinal dosyadaki hedef satırından alınmıştır.

## Hangi problemi çözüyor

Bir mağazanın aylık durumu onlarca ayrı rapora dağılmış hâldedir: satış raporu, P&L, CRM raporu, paket servis platformu raporları, fire ve envanter raporları, eğitim tamamlama listesi, personel devri, şikâyet kayıtları, denetim sonuçları. Bu platform:

- Her raporu kendi sayfasına alır ve mağaza + dönem anahtarıyla tek tabloda birleştirir.
- Her göstergeyi hedefiyle karşılaştırıp yeşil/kırmızı gösterir.
- Mağazaya hedefi tutan göstergelerin katsayıları toplamı kadar puan verir ve mağazaları sıralar. Orijinal sistemde bu puan mağaza müdürlerinin performans notuna dayanak oluyordu.
- P&L sapmasının açıklamasını mağaza satırının yanında gösterir.

Aylık bölge toplantısında sapmalar bu tablo üzerinden konuşulur, aksiyonlar yüz yüze belirlenir.

## Öncesi

Göstergeler, farklı kaynaklardan ayrı ayrı gelen e-postalardaki raporlara tek tek bakılarak takip ediliyordu.

## Sayfalar

| Sayfa | Ne yapar |
|---|---|
| `Nasil_Kullanilir` | Aylık akış, kısaltmalar, renk kodu |
| `Genel_Tablo` | Dönem seçimi; her mağaza tek satırda 21 gösterge, hedef satırı, bölge satırı, puan, sıra, P&L sapma açıklaması |
| `Hedefler` | Her göstergenin yönü (≥ / ≤), hedefi ve performans katsayısı |
| `Performans_Puani` | Gösterge bazında kazanılan puan matrisi, toplam puan ve grafik |
| `Satis` · `PnL` · `CRM` · `Paket_Servis` · `Urun_Karmasi` · `Fire_Envanter` · `Egitim` · `Personel` · `Kahve_Sohbeti` · `Sikayet` · `Denetim` | Kaynak raporların yapıştırıldığı sayfalar |

## Göstergeler ve hedefler

| Grup | Gösterge | Hesap | Hedef |
|---|---|---|---|
| Satış | Satış bütçe sapması | net satış ÷ bütçe − 1 | ≥ %0 |
| P&L | Mağaza katkısı (Line 12) bütçe sapması | (gerçekleşen − bütçe) ÷ \|bütçe\| | ≥ %0 |
| CRM | CRM satış oranı | CRM satışı ÷ net satış | ≥ %14 |
| Paket servis | İptal oranı | iki platformun iptali ÷ işlemi | ≤ %7 |
| Paket servis | Platform açıklık oranı | iki platformun ortalaması | ≥ %90 |
| Ürün karması | Origin espresso oranı | origin espresso ÷ espresso içecek | ≥ %18 |
| Ürün karması | Food attach farkı | (yiyecek ÷ içecek) − geçen yıl | ≥ 0 |
| Fire | Food mark-out oranı | mark-out ÷ yiyecek satışı | ≤ %8 |
| Envanter | Sayım farkı | sayım farkı ÷ net satış | ≥ −%0,5 |
| Ekip | Eğitim tamamlama | tamamlanan ÷ atanan | ≥ %95 |
| Ekip | Turnover | yıl başından ayrılan ÷ ortalama çalışan | ≤ %50 |
| Ekip | Kahve sohbeti farkı | yapılan − (çalışan × 0,2 × 2) | ≥ 0 |
| Misafir | Şikâyet oranı | şikâyet ÷ işlem × 1.000 | ≤ 0,30 |
| Denetim | ASA (genel operasyon) | son denetim puanı | ≥ 90 |
| Denetim | PAP (kayıp önleme) | son denetim puanı | ≥ 85 |
| Denetim | RSA (gıda güvenliği) | son denetim puanı | ≥ 90 |

Mağaza katkısı (Line 12), P&L'in son kalemidir: net satıştan satılan malın maliyeti, royalty, personel, kontrol edilebilir giderler, kira ve amortisman düşüldükten sonra kalan mağaza kârlılığı.

## Performans puanı

Her gösterge için hedef tuttuysa `Hedefler` sayfasındaki katsayı kadar puan, tutmadıysa 0 verilir. Katsayıların toplamı 100'dür; toplam 100 değilse `Hedefler` sayfası uyarır. Verisi olmayan gösterge puanlanmaz. `Genel_Tablo`'da puan 80 ve üzeri yeşil, 60 altı kırmızı görünür.

## Kullanım

Makro yoktur, kurulum gerekmez. `bolge-kpi-platformu.xlsx` Excel 2010 ve sonrası ile LibreOffice'te açılır.

1. Her ay sistem raporlarını ilgili kaynak sayfaya yapıştırın. Veri **B sütunundan** başlar: dönem kodu (P1–P12), mağaza adı, rapor sütunları. A sütunu anahtar formülüdür; yeni satırlara aşağı kopyalayın.
2. `Genel_Tablo` > B1'den dönemi seçin.
3. Toplantıda `Genel_Tablo` ve `Performans_Puani` üzerinden sapmaları değerlendirin.

Örnek dosyada P1–P3 dönemleri ve 8 mağaza vardır.

## Kendi verinize uyarlama

| Nerede | Ne değiştirilir |
|---|---|
| `Genel_Tablo` A–B sütunları | Mağaza adları ve formatları; kaynak sayfalardaki yazımla aynı olmalı |
| `Hedefler` | Hedefler, yönler, katsayılar |
| Kaynak sayfalar | Rapor sütun sırası farklıysa `Genel_Tablo` formüllerindeki sütun harfleri |

Yeni mağaza eklemek için `Genel_Tablo` ve `Performans_Puani` sayfalarında bir satırı kopyalayıp aşağıya ekleyin ve bölge satırının aralıklarını genişletin.

## Sınırlar

- Raporlar kaynak sistemlerden elle yapıştırılır; otomatik veri çekme yoktur.
- Aksiyonlar toplantıda belirlendiği için dosyada aksiyon takip sayfası yoktur.
- Yıl başından toplamlar (YTD) yalnızca turnover için kaynak raporda hazır gelir; diğer göstergeler seçilen ayın değeridir.

## Lisans

MIT. Ayrıntılar için `LICENSE` dosyasına bakın.
