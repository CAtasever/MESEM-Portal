
# MESEM Portal

MESEM (Mesleki Eğitim Merkezi) öğrenci, işletme ve koordinatör öğretmen kayıtlarını yönetmek; işletme adreslerini bölgelere ayırmak ve haftalık işletme ziyaret planı üretmek için geliştirilmiş **tek dosyalık, sunucusuz** bir web uygulamasıdır.

**Güncel sürüm: v5.27**

- Tek bir `.html` dosyasıdır; kurulum, sunucu, veritabanı veya hesap gerektirmez.
- Tüm veri **yalnızca kullanıcının tarayıcısında** (`localStorage`) tutulur. Hiçbir veri bir sunucuya gönderilmez.
- Arayüz Türkçedir.

---

## İçindekiler

1. [Özellikler](#özellikler)
2. [Hızlı başlangıç](#hızlı-başlangıç)
3. [Sekmeler](#sekmeler)
4. [Excel içe aktarma](#excel-içe-aktarma)
5. [Bölge kuralları](#bölge-kuralları)
6. [Haftalık planlama ve İME](#haftalık-planlama-ve-ime)
7. [Yedekleme ve geri yükleme](#yedekleme-ve-geri-yükleme)
8. [Veri depolama (localStorage)](#veri-depolama-localstorage)
9. [Kullanılan kütüphaneler](#kullanılan-kütüphaneler)
10. [Bilinen sınırlar](#bilinen-sınırlar)
11. [Sürüm notları](#sürüm-notları)
12. [Geliştirici notları](#geliştirici-notları)

---

## Özellikler

- **Kayıt yönetimi:** Öğrenci, sınıf/şube, dal, koordinatör öğretmen, işletme, adres, telefonlar, usta öğretici, not ve koordinat bilgileri.
- **Excel içe aktarma / dışa aktarma:** Mevcut listeyi güncelleyerek veya yeni kayıt ekleyerek içe aktarır; filtrelenmiş listeyi Excel olarak indirir.
- **Otomatik bölge atama:** Adres metnindeki anahtar kelimelere göre bölge belirlenir. Kurallar kullanıcı tarafından düzenlenir.
- **Toplu öğretmen değiştirme:** Seçili kayıtların öğretmenini tek seferde değiştirir; son işlem geri alınabilir.
- **İstatistik:** Alan, dal, öğretmen ve bölge dağılımı; yazdırılabilir.
- **İşletme konum görünümü:** Adres ve koordinata göre harita bağlantıları, cihaz konumu ile yakınlık için "Konumum" düğmesi.
- **Haftalık planlama:** Öğretmen ve ay seçilerek haftalık ziyaret planı üretilir; yakın adresler aynı güne toplanabilir, resmi tatiller dikkate alınır, "Otomatik Gün Öner" ile her hafta için uygun gün denenir.
- **İME desteği:** İşletmede Mesleki Eğitim (İME) gün/saat pencereleri ve haftalık kapalı haftalar planlamaya yansır.
- **Çıktılar:** Plan önizleme ve yazdırma, planı Excel olarak indirme, **Görev Teslim Listesi** (bu hafta / tüm haftalar), QR kodlu harita bağlantıları.
- **Arşiv:** Kayıtlar silinmeden arşive alınır ve geri getirilebilir.
- **Yedek:** Tek JSON dosyasıyla kayıtlar, kurallar, İME ayarları ve tatiller yedeklenir.
- **Mobil uyumlu** arayüz; büyük listelerde sayfalama ("Daha fazla göster").
- **Çoklu sekme eşitleme:** Aynı tarayıcıda başka sekmede yapılan değişiklik açık sekmeye otomatik yansır.

---

## Hızlı başlangıç

1. `mesem_portal_v5_27.html` dosyasını indirin.
2. Dosyayı modern bir tarayıcıda (Chrome, Edge, Firefox, Safari) açın.
3. **Liste** sekmesinden Excel dosyanızı içe aktarın veya kayıtları elle ekleyin.
4. **Kurallar** sekmesinde bölge kurallarını kontrol edin.
5. **Haftalık Planlama** sekmesinde öğretmeni ve ayı seçip planı oluşturun.
6. Düzenli olarak **Yedek Al** ile yedek indirin.

> **İnternet bağlantısı gerekir:** Excel, QR ve simge kütüphaneleri CDN'den yüklenir (bkz. [Kullanılan kütüphaneler](#kullanılan-kütüphaneler)). Kayıt verisi ise internetsiz de çalışır, ancak kütüphaneler yüklenmezse Excel ve QR işlevleri çalışmaz.

> **Önemli:** Veri tarayıcıya özeldir. Tarayıcı verilerini temizlemek, farklı tarayıcı/profil/cihaz kullanmak veya dosyayı farklı bir adresten (ör. `file://` yerine bir sunucudan) açmak farklı bir depo anlamına gelir. Yedek almadan tarayıcı verisini silmeyin.

---

## Sekmeler

| Sekme | İşlev |
|---|---|
| **Liste** | Ana kayıt tablosu: arama, çoklu filtre (öğretmen, bölge, sınıf, şube, alan, dal), sıralama, düzenleme, arşive alma, toplu öğretmen değiştirme, Excel/Yedek işlemleri. |
| **İstatistik** | Alan, dal, öğretmen ve bölgelere göre dağılım ve özet göstergeler; yazdırma düzeni ve yönü seçilebilir. |
| **İşletme Konum** | İşletmeleri adres/koordinat bilgisiyle listeler; harita bağlantısı ve "Konumum" desteği. |
| **Haftalık Planlama** | Plan ayarları, resmi tatiller, İME ayarları, plan üretimi, önizleme, yazdırma, Excel ve Teslim Listesi çıktıları. |
| **Kurallar** | Bölge kurallarını ekleme, düzenleme, indirme, içe aktarma ve toplu silme. |
| **Arşiv** | Arşivlenen kayıtlar; arama tüm arşivde çalışır, çizim sayfalıdır. |

---

## Excel içe aktarma

İlk sayfa (sheet) okunur. Sütun başlıkları esnektir; aşağıdaki adlardan biri yeterlidir (büyük/küçük harf ve baştaki/sondaki boşluklar önemsenmez):

| Alan | Kabul edilen başlıklar |
|---|---|
| Id | `Id`, `id`, `ID` |
| Öğrenci Id | `Öğr.Id`, `Ogr.Id`, `Öğrenci Id` |
| Öğrenci No | `Öğr.No`, `Öğrenci No`, `Ogr.No`, `ogrNo`, `No`, `Numara` |
| Ad Soyad | `Ad Soyad`, `Adı Soyadı`, `Öğrenci Adı`, `İsim`, `adSoyad` |
| Sınıf | `Sınıf`, `Sınıfı`, `sinif` |
| Şube | `Şube`, `Sube`, `Şubesi`, `sube` |
| Dal | `Dal`, `Dalı`, `Alan/Dal`, `dal` |
| Öğretmen | `Öğretmen`, `Koordinatör Öğretmen`, `ogretmen` |
| İşletme | `Firma`, `Firma Adı`, `Tespit Edilen Firma`, `İşletme`, `İşletme Adı`, `isletme` |
| Adres | `Adres`, `Temiz Adres`, `İşyeri Adresi`, `İşletme Adresi`, `adres` |
| Koordinat | `Koordinat`, `Konum`, `koordinat` |
| Not | `Not`, `Notlar`, `notlar` |
| Öğrenci telefonu | `Öğrenci Tel`, `Öğr. Tel`, `Ogr Tel`, `Telefon`, `Tel` |
| İşyeri telefonu | `İşyeri Tel`, `İşletme Tel`, `Firma Tel` |
| Usta öğretici | `Usta Öğretici`, `Usta Ogretici`, `Eğitici Personel`, `Usta` |

**Eşleştirme sırası (mevcut kayıtlarla):**

1. `Id` (varsa ve `Öğr.Id` çelişmiyorsa)
2. `Öğr.Id`
3. `Öğr.No`
4. Hiçbir kimlik yoksa: ad + işletme + sınıf + şube

Aynı dosyada bir kayıt ikinci kez eşleşmez; bu sayede aynı öğrencinin farklı işletmelerdeki satırları ayrı kalır. Eşleşen kayıtta yalnızca Excel'de **dolu olan** alanlar güncellenir; boş hücreler mevcut değeri silmez. Adres değişirse o kaydın elle seçilmiş bölgesi sıfırlanır ve bölge yeniden hesaplanır.

**Onay akışı (v5.27):** Dosya okunduktan sonra "kaç satır okundu / kaç yeni / kaç güncelleme" özeti ve varsa **şube bilgisi eksik** uyarısı gösterilir.

- **Onaylarsanız:** bölgeler hesaplanır, liste çizilir ve veri kaydedilir.
- **İptal ederseniz:** hiçbir şey kaydedilmez, liste olduğu gibi kalır. Sayfayı yenileseniz de içe aktarma geri gelmez.
- **Hata olursa:** bellekteki yarım değişiklikler geri alınır; tarayıcıya hiçbir şey yazılmaz.

> `Şube` bilgisi, Haftalık Planlama'da günün belirlenmesi için gereklidir. Şubesi boş kayıtlar planda "gün belirsiz ⚠" olarak işaretlenir.

---

## Bölge kuralları

Her kural bir **ad**, bir **anahtar kelime listesi** ve isteğe bağlı bir **küme** değerinden oluşur. Adres metni kurallara sırayla uygulanır; ilk eşleşen kuralın adı kaydın bölgesi olur. Eşleşme bulunamazsa bölge `Belirtilmemiş / Diğer` olur.

- Kurallar tek tek aktif/pasif yapılabilir.
- **İndir** ile kurallar dosyaya alınır, **içe aktar** ile geri yüklenir.
- Kayıt düzenleme penceresinde bölge **elle** de seçilebilir; elle seçilen bölge, adres değişmedikçe kural değişikliklerinden etkilenmez.
- Kural değiştiğinde tüm kayıtların bölgesi yeniden hesaplanır.

---

## Haftalık planlama ve İME

**Plan ayarları**

- **Öğretmen seçimi** ve **planlanacak ay**
- **Yakın adresleri aynı güne toplama:** Aynı kümedeki/yakın adresler aynı güne yerleştirilir.
- **Resmi tatiller:** Eklenen günler planlamada atlanır.
- **Otomatik Gün Öner:** Her hafta için en uygun günü dener.

**İME ayarları**

- İME açık/kapalı anahtarı
- Pazartesi–Cuma için gün bazlı başlangıç/bitiş saati (çalışma penceresi **09:00–17:00** ile sınırlıdır)
- Ziyaret süresi (dakika; varsayılan 40)
- Belirli haftaları **kapalı** işaretleme

**Çıktılar**

- Önizleme ve yazdırma
- Planı Excel olarak indirme
- **Görev Teslim Listesi:** seçili hafta için tek sayfa veya tüm haftalar için ayrı sayfalar; işletme konumları için QR kodlu Google Maps bağlantıları içerir.

---

## Yedekleme ve geri yükleme

### Yedek Al

**Liste** sekmesindeki **Yedek Al** düğmesi `MESEM_Yedek_YYYY-AA-GG.json` dosyasını indirir. Arşivlenmiş kayıtlar dahil **tüm** veriyi içerir.

Yedek dosyası şu yapıdadır:

```json
{
  "version": "birlesik1",
  "date": "2026-10-17T12:00:00.000Z",
  "records": [ ],
  "rules":   [ ],
  "ime":     { "on": true, "days": { "1": { "s": "09:00", "e": "17:00" } }, "visit": 40, "off": [ ] },
  "holidays": [ "2026-10-29" ]
}
```

| Alan | İçerik | İlgili localStorage anahtarı |
|---|---|---|
| `version` | Yedek biçimi. **`birlesik1` olarak sabit kalır**; yeni alanlar geri uyumludur. | — |
| `date` | Yedeğin alındığı an (ISO) | — |
| `records` | Tüm öğrenci/işletme kayıtları (arşiv dahil) | `mesemRecordsBirlesikV1` |
| `rules` | Bölge kuralları | `mesemRulesBirlesikV1` |
| `ime` | İME gün/saat, ziyaret süresi, kapalı haftalar | `mesemImeBirlesikV2` |
| `holidays` | Resmi tatil günleri | `mesemHolidaysBirlesikV1` |

### Yedek Yükle

**Yedek Yükle** ile bir `.json` yedek seçilir. Yükleme öncesi, kaç kayıt ve kuralın yükleneceği ile İME/tatil bilgisinin gelip gelmediği onay penceresinde belirtilir.

- **Mevcut kayıt ve kurallar değiştirilir** (silinip yedektekiler yüklenir).
- **Eski yedekler** (`ime` / `holidays` alanı olmayanlar) sorunsuz yüklenir. Bu durumda mevcut İME ayarlarınıza ve tatillerinize **dokunulmaz** (kısmi geri yükleme).
- Yedekte `ime` / `holidays` varsa bunlar hem belleğe hem de `localStorage`'a yazılır.
- **İME verisi doğrulanır (v5.27):** Yalnızca geçerli `SS:DD` saat değerleri ve metin tipindeki kapalı hafta kayıtları alınır; bozuk bir yedek İME ekranını bozmaz.
- Geçersiz veya bozuk dosya reddedilir.

### Tüm sistemi sıfırlama

Ayarlardaki sıfırlama işlemi önce otomatik olarak bir yedek indirir, ardından kayıtları, kuralları, İME ayarlarını, tatilleri ve geri alma verisini siler ve sayfayı yeniler.

---

## Veri depolama (localStorage)

| Anahtar | İçerik | Yedekte |
|---|---|---|
| `mesemRecordsBirlesikV1` | Tüm kayıtlar | ✔ `records` |
| `mesemRulesBirlesikV1` | Bölge kuralları | ✔ `rules` |
| `mesemImeBirlesikV2` | İME ayarları (`on`, `days`, `visit`, `off`) | ✔ `ime` |
| `mesemHolidaysBirlesikV1` | Resmi tatil listesi | ✔ `holidays` |
| `mesemBulkUndoV1` | Son toplu öğretmen değişikliğini geri almak için veri | ✘ |
| `mesemLastBackupV1` | Son yedek alma zamanı | ✘ |
| `mesemRecordsV23`, `mesemRulesV23` | Eski sürüm verisi; yalnızca yedek/geçiş amaçlı okunur | ✘ |
| `mesemImeBirlesikV1` | Eski İME anahtarı; yalnızca sıfırlamada temizlenir | ✘ |

**Kota:** Tarayıcı deposu sınırlıdır (genellikle birkaç MB). Yazma başarısız olursa uygulama sessiz kalmaz; kota dolduysa şu uyarı gösterilir: *"Tarayıcı deposu doldu. Yedek Al, sonra gerekirse arşiv/kayıt azaltın."* Diğer yazma hataları için genel bir uyarı çıkar. Bu durumda önce **Yedek Al** yapın.

**Sekmeler arası eşitleme:** Aynı tarayıcıda uygulama birden fazla sekmede açıksa, bir sekmede kayıt/kural/İME/tatil değişince diğer sekmeler kısa bir gecikmeyle (≈150 ms) verileri yeniden yükler ve "Veri başka bir sekmeden güncellendi." bildirimini gösterir. Eşitleme depoya yazmadığı için sonsuz döngü oluşmaz.

---

## Kullanılan kütüphaneler

Tümü `cdnjs.cloudflare.com` üzerinden yüklenir; dosya yerelde de çalışır, ancak ilk açılışta (veya önbellek yokken) internet gerekir.

| Kütüphane | Sürüm | Kullanım |
|---|---|---|
| [SheetJS (xlsx)](https://sheetjs.com/) | 0.18.5 | Excel içe/dışa aktarma |
| [ExcelJS](https://github.com/exceljs/exceljs) | 4.4.0 | Plan ve Teslim Listesi Excel çıktıları |
| [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) | 1.0.3 | Harita bağlantıları için QR kod |
| [Font Awesome](https://fontawesome.com/) | 6.4.0 | Simgeler |

---

## Bilinen sınırlar

- Sunucu, kullanıcı hesabı veya oturum yoktur; veriye dosyaya erişimi olan herkes erişebilir. Hassas kişisel veriler (öğrenci/telefon) için cihaz güvenliğine dikkat edin.
- Veri tarayıcıya bağlıdır; cihazlar arası otomatik eşitleme yoktur. Cihaz değiştirmek için yedek kullanın.
- Tek dosya mimarisi nedeniyle kod modüllere bölünmemiştir.
- Excel/QR/simge kütüphaneleri CDN'den yüklenir; çevrimdışı ilk açılışta bu işlevler çalışmayabilir.
- `Yedek Yükle`, mevcut kayıt ve kuralları değiştirir; yüklemeden önce güncel bir yedek almanız önerilir.

---

## Sürüm notları

### v5.27
- **Excel içe aktarma:** Onay penceresi açıkken liste artık değişmiş halde görünmüyor; bölge hesabı ve çizim yalnızca onaydan sonra yapılıyor.
- **Excel iptali:** İptalde depoya yeniden yazma yapılmıyor; gereksiz yazmadan doğan yanlış kota uyarısı giderildi.
- **Yedek yükleme:** İME verisi doğrulanıyor (geçersiz saat/gün değerleri alınmıyor).
- **Depolama uyarıları:** Son yedek zamanı ve toplu değişiklik geri alma verisi yazılırken oluşan hatalar artık sessizce yutulmuyor.

### v5.26
- **Excel içe aktarma hata yolu:** İşlem sırasında hata olursa bellekteki yarım değişiklikler geri alınıyor; sonraki bir kayıtla kalıcı hale gelmesi engellendi.

### v5.25
- **Yedek kapsamı:** JSON yedeğe İME ayarları (`ime`) ve resmi tatiller (`holidays`) eklendi. Eski yedekler geri uyumlu olarak yüklenir.
- **Excel iptali:** İçe aktarma iptalinde sayfa yenilense bile içe aktarılan verinin geri gelmesi düzeltildi.
- **Arşiv sayfalama:** Arşiv listesi ana liste gibi sayfalı çiziliyor; arama tüm arşivde çalışıyor.
- **Depolama kotası:** Kota dolduğunda net uyarı gösteriliyor.
- **Sekme eşitleme:** Başka sekmede yapılan değişiklikler otomatik yansıtılıyor.

### v5.24
- Sekme geçiş önbelleği: Veri değişmediyse sekme yeniden çizilmez.

---

## Geliştirici notları

- **Mimari:** Tek HTML dosyası; stil, işaretleme ve betik aynı dosyada. Derleme veya paket yöneticisi yoktur.
- **Satır sonu:** Dosya **CRLF** satır sonlarıyla tutulur.
- **Sürüm numarası 3 yerde birlikte güncellenmelidir:**
  1. Dosyanın ilk satırındaki başlık yorumu
  2. `<title>` etiketi
  3. Sayfadaki `#homeLink` içindeki küçük sürüm rozeti (`<span>`)
- **Sözdizimi kontrolü:** `<script>` içeriğini ayrı bir dosyaya çıkarıp `node --check` ile doğrulayın.
- **Yedek biçimi:** `version` alanı `birlesik1` olarak kalır; yeni alanlar yalnızca eklenir, mevcut alanlar değiştirilmez.
- **Kapsam dışı (bilinçli kararlar):** Modüllere bölme, backend, kimlik/oturum, IndexedDB'ye geçiş, CSP ve kütüphanelerin CDN dışına alınması.
- **Planlanan iyileştirmeler:** SheetJS/ExcelJS sadeleştirme, CDN SRI (bütünlük) özniteliği, harici bağlantılarda `rel=noopener` taraması.

---

## Lisans

Lisans bilgisi eklenmemiştir. Depoyu herkese açık yayınlayacaksanız bir lisans seçip bu bölümü güncelleyin (ör. MIT).
