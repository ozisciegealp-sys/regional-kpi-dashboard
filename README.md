# Bölge KPI Kontrol Platformu

**Türkçe** | [English](README.en.md)

Çok mağazalı bir bölgenin satış, P&L (kârlılık), CRM, paket servis, ürün karması, fire, envanter, eğitim, personel devri, müşteri şikâyeti ve denetim verilerini **tek tabloda** birleştiren, hedefe göre renklendirerek her mağazaya **100 üzerinden performans puanı** veren ve dönemler arası **Yıldızlar Ligi** sıralamasını üreten Excel platformu.

> **Gizlilik ve Sentetik Veri Notu:** Bu çalışma kitabı, 16 mağazalık bölge operasyonunda kurduğum ve aylık kontrollerini yürüttüğüm online Excel platformunun **tamamen sentetik (kurgu) veriyle** yeniden kurulmuş sürümüdür. Kurumsal gizlilik gereği hiçbir marka, gerçek mağaza adı veya finansal şirket verisi yer almaz; örnek dosyada 8 kurgu mağaza (`Mağaza A`–`Mağaza H`) ve 3 dönem (`P1`–`P3`) modellenmiştir.

## Hangi problemi çözüyor

Bir mağazanın aylık performansı normalde onlarca ayrı rapora dağılmış hâldedir: satış raporu, P&L tablosu, CRM raporu, paket servis platform verileri, fire ve envanter sayım sonuçları, eğitim tamamlama listeleri, İK personel devri, müşteri şikâyet kayıtları ve denetim raporları. Bu platform:

- 11 ayrı kaynak raporu kendi sayfasına alır ve `Dönem|Mağaza` anahtarıyla tek genel tabloda birleştirir.
- **16 puanlanan operasyonel KPI**'ı hedef eşikleriyle karşılaştırıp yeşil/kırmızı koşullu biçimlendirmeyle işaretler; yanında **5 bağlam göstergesini** (`ADT`, `Net Satış`, `Mağaza Katkısı TL`, `Paket Satış Payı %`, `Food Attach %`) aynı satırda sunar (toplam 21 gösterge sütunu).
- Hedefi tutan KPI'ların ağırlık katsayılarını toplayarak her mağazaya 100 üzerinden performans puanı verir ve sıralar.
- **`Yildizlar_Ligi`** sayfasında P1–P3 dönemlerinin kümülatif puan ortalamasını, mağaza ciro kademesini (`Tier 1–3`), son ay trendini ve lig grubunu (`Altın / Gümüş / Gelişim Ligi`) izler.
- P&L sapma açıklamalarını doğrudan mağaza satırının yanında gösterir; aylık toplantıda sapmalar mağaza bazında aksiyona bağlanır.

## Öncesi

Göstergeler, farklı departmanlardan ayrı ayrı gelen rapor ve e-postalara tek tek bakılarak dağınık şekilde takip ediliyordu.

## Sayfalar

| Sayfa | Ne yapar |
|---|---|
| `Nasil_Kullanilir` | Aylık çalışma akışı, kısaltmalar ve renk kodu |
| `Genel_Tablo` | Dönem seçimi (`P1–P12`); her mağaza tek satırda 16 puanlanan KPI + 5 bağlam göstergesi (21 sütun), hedef satırı, bölge özeti, puan, sıra ve P&L sapma açıklaması |
| `Performans_Puani` | Seçili dönemde KPI bazında kazanılan puan matrisi, toplam puan ve karşılaştırma grafiği |
| `Yildizlar_Ligi` | P1–P3 dönem puanları, dönem ortalaması, son ay trendi, ciro kademesi (`Tier`), lig grubu, kümülatif satış/kârlılık ve grafik |
| `Hedefler` | Puanlanan 16 KPI'ın yönü (`≥` / `≤`), hedef eşiği ve 100 toplamlı ağırlık katsayıları |
| `Satis` · `PnL` · `CRM` · `Paket_Servis` · `Urun_Karmasi` · `Fire_Envanter` · `Egitim` · `Personel` · `Kahve_Sohbeti` · `Sikayet` · `Denetim` | Kaynak sistem raporlarının yapıştırıldığı 11 veri sayfası |

## Puanlanan 16 KPI ve örnek hedefler

| Grup | Gösterge | Hesap | Hedef |
|---|---|---|---|
| Satış | Satış bütçe sapması | net satış ÷ bütçe − 1 | ≥ %0,0 |
| P&L | Mağaza katkısı (Line 12) bütçe sapması | (gerçekleşen − bütçe) ÷ \|bütçe\| | ≥ %0,0 |
| CRM | CRM satış oranı | CRM satışı ÷ net satış | ≥ %14,0 |
| Paket servis | İptal oranı | iki platform toplam iptali ÷ işlemi | ≤ %7,0 |
| Paket servis | Platform açıklık oranı | iki platform açıklık ortalaması | ≥ %90,0 |
| Ürün karması | Origin espresso oranı | origin espresso ÷ toplam espresso içecek | ≥ %18,0 |
| Ürün karması | Food attach geçen yıla farkı | (yiyecek ÷ içecek) − geçen yıl oranı | ≥ %0,0 |
| Fire | Food mark-out oranı | mark-out tutarı ÷ yiyecek satışı | ≤ %8,0 |
| Envanter | Envanter sayım farkı | sayım farkı ÷ net satış | ≥ −%0,50 |
| Ekip | Eğitim tamamlama oranı | tamamlanan ÷ atanan eğitim | ≥ %95 |
| Ekip | Turnover (YTD) | yıl başından ayrılan ÷ ortalama çalışan | ≤ %50 |
| Ekip | Ekip gelişim / kahve sohbeti farkı | yapılan − dönem hedefi | ≥ 0 |
| Misafir | Şikâyet oranı | şikâyet adedi ÷ işlem × 1.000 | ≤ 0,30 |
| Denetim | ASA (genel operasyon) | son denetim puanı | ≥ 90 |
| Denetim | PAP (kayıp önleme) | son denetim puanı | ≥ 85 |
| Denetim | RSA (gıda güvenliği) | son denetim puanı | ≥ 90 |

## Kullanım

Makro içermez; `bolge-kpi-platformu.xlsx` Excel 2010+ ve LibreOffice'te doğrudan açılır.

1. Aylık kaynak raporları ilgili veri sayfalarına **B sütunundan** başlayarak yapıştırın ve A sütunundaki anahtar formülünü (`=B2&"|"&C2`) aşağı kopyalayın.
2. `Genel_Tablo` > `B1` hücresinden dönemi (`P1`, `P2`, `P3`…) seçin.
3. Aylık sapmaları `Genel_Tablo` ve `Performans_Puani`, kümülatif dönem gidişatını `Yildizlar_Ligi` üzerinden değerlendirin.

## Lisans

MIT. Ayrıntılar için `LICENSE` dosyasına bakın.
