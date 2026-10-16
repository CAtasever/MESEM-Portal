# MESEM Portal

MESEM (Mesleki Eğitim) öğrencilerinin işletme yerleştirme, haftalık ziyaret planlama ve takip süreçlerini yöneten, **tek dosyalık** bir web uygulamasıdır. Sunucu gerektirmez; tüm veriler tarayıcının `localStorage` alanında saklanır.

Güncel sürüm: **v4.7**

## Özellikler

- **Liste:** Öğrenci kayıtlarını arama, çoklu filtre (öğretmen, sınıf, şube, dal, bölge) ve sütun sıralama ile yönetme. Kayıtlar 100'lük parçalar halinde çizilir ("Daha fazla göster"); arama ve filtreler tüm kayıtlar üzerinde çalışır.
- **Düzenleme ve arşiv:** Kayıt düzenleme, arşive alma ve geri alma.
- **İşletme Konum:** İşletme bazında koordinat girme (düz koordinat veya Google Maps bağlantısı), bulunulan konumu alma, Türkiye sınırları dışındaki değerleri uyarma, çakışan konumları filtreleme.
- **Bölge kuralları:** Adres anahtar kelimelerine göre otomatik bölge atama; kural ekleme, düzenleme, sıralama, etkinleştirme ve dışa/içe aktarma.
- **Haftalık planlama:** Öğretmen ve ay seçimine göre haftalık işletme ziyaret planı oluşturma. İş yeri ziyareti için **İME (İşletmede Mesleki Eğitim) saat penceresi** (09:00–17:00, öğle arası 11:50–12:40 düşülür) kullanılabilir. Plan üzerinde işletmeyi başka haftaya taşıma ve kapasite dengeleme.
- **Yazdırma ve önizleme:** Liste ve planlar A4 yatay/dikey yazdırılır; plan çıktısı tek sayfaya sığdırılır, QR kodu ve imza alanı içerir.
- **Dışa aktarma:** Excel (liste, teslim listesi), JSON yedek ve kural dosyası.
- **Excel içe aktarma:** Mevcut verilere ekleme/güncelleme.

## Kullanılan teknolojiler

- HTML, CSS, JavaScript (tek dosya, derleme adımı yok)
- Yalnızca CDN üzerinden yüklenen kütüphaneler:
  - [SheetJS (xlsx)](https://sheetjs.com/)
  - [ExcelJS](https://github.com/exceljs/exceljs)
  - [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator)
  - [Font Awesome 6](https://fontawesome.com/)

## Kurulum ve kullanım

1. Depoyu klonlayın veya `mesem_portal_v4.7.html` dosyasını indirin.
2. Dosyayı modern bir tarayıcıda (Chrome, Edge, Firefox, Safari) açın. İnternet bağlantısı yalnızca ilk yüklemede kütüphaneler için gereklidir.
3. **Excel Yükle** ile öğrenci listesini içe aktarın.
4. Düzenli olarak **Yedek Al** ile JSON yedeği indirin; veriler yalnızca bu tarayıcıda tutulur.

> **Not:** Tarayıcı verisini temizlemek (önbellek/site verisi silme) kayıtları siler. Yedek almadan bu işlemi yapmayın.

## Veri saklama

| Anahtar | İçerik |
|---|---|
| `mesemRecordsBirlesikV1` | Öğrenci ve işletme kayıtları |
| `mesemImeBirlesikV2` | İME saat ve ziyaret ayarları |
| `mesemHolidaysBirlesikV1` | Tatil günleri |

Yedek dosyası sürüm etiketi `birlesik1` olarak yazılır; bu değer uyumluluk için değiştirilmez.

## Sürüm geçmişi (özet)

- **v4.7** – İME saat seçicileri 09:00–17:00 ile sınırlandı; eski kayıtlar kırpılır.
- **v4.6** – İME varsayılanı Pazartesi–Cuma 09:00–17:00; öğle arası 11:50–12:40.
- **v4.5** – Plan yazdırma ve önizleme taşması giderildi; sığdırma algoritması iyileştirildi.
- **v4.4** – Liste yazdırmada alt bilgi ve kelime kırılmaları düzeltildi.
- **v4.3** – Liste ve konum sayfa boyutu 100.
- **v4.2** – Mobil uyumluluk (dokunma alanları, konum kartları, iOS girdi boyutu).
- **v4.1** – İşletme Konum: sayfalama, GPS, uyarılar, anında tazeleme.
- **v4.0** – Ana liste sayfalaması ve yazdırma düzeltmesi; sürüm etiketi.

## Bilinen sınırlamalar

- Planlama yazdırması gerçek verilerle ve farklı yazıcılarda tam olarak doğrulanmadı.
- Dikey yazdırmada liste sütunları sıkışık olabilir.
- Arşiv listesi henüz sayfalanmıyor.
- Mobil cihazlarda test sınırlı; dokunma ve yazdırma davranışı cihaza göre değişebilir.

## Lisans

Lisans henüz belirlenmedi. Yayımlamadan önce bir `LICENSE` dosyası eklenmelidir.
