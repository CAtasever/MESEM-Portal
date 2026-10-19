<div align="center">

# 🏢 MESEM Portal (v5.32)

**Mesleki Eğitim Merkezleri (MESEM) için Koordinatör Öğretmen Ziyaret Planlama, İşletme Konum Yönetimi, İME ve Görev Takip Sistemi**

![Sürüm](https://img.shields.io/badge/S%C3%BCr%C3%BCm-v5.32-10b981?style=for-the-badge)
![Mimari](https://img.shields.io/badge/Mimari-Tek%20Dosya%20(Sunucusuz)-1e3a8a?style=for-the-badge)
![Veri Güvenliği](https://img.shields.io/badge/Veri-%25100%20Yerel%20(KVKK%20Dostu)-f59e0b?style=for-the-badge)
![Mobil Uyum](https://img.shields.io/badge/Mobil-Tam%20Uyumlu-3b82f6?style=for-the-badge)

</div>

---

## 📖 Proje Hakkında

**MESEM Portal**; koordinatör öğretmenlerin işletmelerdeki çırak ve kalfa öğrencilerini takip etmesini, işletmelerin harita konumlarını tek merkezden yönetmesini, birbirine yakın dükkanları aynı güne toplayan akıllı ziyaret rotaları çıkarmasını ve resmi evrakları (**Karekodlu Ziyaret Çizelgesi**, **Görev Teslim Listesi**) tek tıkla hazırlamasını sağlayan **sunucusuz, tek dosyalı (`index.html`)** bir web uygulamasıdır.

Hiçbir kurulum, veritabanı, üyelik veya şifre gerektirmez; bilgisayarda ve cep telefonunda doğrudan çalışır.

---

## 🛡️ 1. En Önemli Özellik: Lokal Veri (Bilgileriniz Sadece Sizin Cihazınızda!)

> [!IMPORTANT]
> **Verileriniz İnternete Gitmez & Yedek Alma Şarttır!**
> Bu sistem internetteki yabancı bir sunucuya veya buluta **asla veri göndermez**. Yüklediğiniz öğrenci listeleri, telefon numaraları, notlar ve dükkan konumları sadece o an kullandığınız bilgisayarın veya telefonun kendi tarayıcı hafızasında (`localStorage`) durur.

1. **Gizlilik ve KVKK:** Öğrenci ve işletme verileri cihazınızdan dışarı çıkmadığı için %100 güvenlidir.
2. **Aman "Yedek Al"mayı Unutmayın:** Bilgisayar temizliği yapıldığında, format atıldığında veya tarayıcı geçmişi silindiğinde bilgileriniz uçmasın diye işiniz bittiğinde sağ üstteki **"Yedek Al"** düğmesine basıp `.json` yedek dosyanızı bilgisayarınıza indirin (7 gün yedek alınmazsa sistem sizi otomatik uyarır).
3. **Başka Bilgisayara veya Telefona Taşıma:** Evdeki bilgisayardan okuldakine (veya cep telefonunuza) geçeceğiniz zaman, indirdiğiniz yedek dosyasını **"Yedek Yükle"** düğmesiyle seçmeniz yeterlidir; tüm listeniz ve harita konumlarınız saniyeler içinde geri gelir.
4. **Sekmeler Arası Canlı Senkronizasyon:** Portal aynı tarayıcıda birden fazla sekmede açıksa, bir sekmede yaptığınız değişiklik diğer sekmeye anında yansır.

---

## 📍 2. İşletme Konum Modülü (Sahadaki En Büyük Kolaylık)

Koordinatör öğretmenlerin en çok vakit kaybettiği "adres arama ve konum tutturma" sorununu kökten çözen merkezi modüldür:

* **Aynı Dükkana Tek İşlem:** Bir tamirhanede veya fabrikada birden fazla çırak öğrenciniz varsa tek tek uğraşmazsınız. **İşletme Konum** sekmesinde her dükkan tek bir satırda görünür; konumu bir kere kaydettiğinizde o dükkanda çalışan **tüm öğrencilerin kayıtlarına otomatik işlenir**.
* **Dükkandayken Tek Tuşla "Konumum" (GPS):** İşletmeye ziyarete gittiğinizde cep telefonunuzdan portala girip **"Konumum"** düğmesine basmanız yeterlidir. Telefonunuzun GPS'i bulunduğunuz dükkanın tam noktasını (`41.0082, 28.9784`) haritaya eliyle koymuş gibi kaydeder.
* **Harita Linki Yapıştırma:** Dilerseniz Google Haritalar'dan kopyaladığınız uzun harita linkini veya koordinatı doğrudan kutucuğa yapıştırabilirsiniz; sistem koordinatı içinden otomatik ayıklar.
* **Eksik ve Hatalı Konumları Yakalama:**
  * **"Yalnızca konumsuz"** filtresiyle haritası henüz girilmemiş dükkanları tek tıkla listeleyebilirsiniz.
  * **"Çakışan konumlar"** filtresiyle farklı satırlarda farklı koordinat kalmış işletmeleri tespit edebilirsiniz.
  * Türkiye sınırları dışına taşan hatalı koordinat girişlerinde sistem sizi sarı ikazla uyarır.

---

## 🧭 3. Tüm Modüller ve Kullanım Rehberi

### 📋 Ana Liste ve Toplu İşlemler
* **Excel'den Tek Tıkla Aktarma:** İdareden alınan öğrenci-işletme Excel listesini **"Excel Yükle"** ile içeri atabilirsiniz. Öğrenci No veya Id üzerinden mevcut kayıtları tanır, mükerrer kayıt açmaz, sadece değişen bilgileri günceller.
* **Toplu Öğretmen Değiştirme:** Görev değişikliği olduğunda tablodan istediğiniz öğrencileri seçip tek tuşla yeni koordinatör öğretmenine atayabilirsiniz. Yanlışlıkla yaparsanız **"Son değişikliği geri al"** düğmesiyle işlemi anında geri alabilirsiniz.
* **Çoklu Filtreleme ve Sabit Sütunlar:** Öğretmen, Bölge, Sınıf, Şube, Alan ve Dal bazında çoklu filtreleme yapabilirsiniz. Tabloyu sağa kaydırdığınızda öğrenci adı sabit kalır, satırı kaybetmezsiniz.

### 📅 Akıllı Haftalık Planlama & İME Saatleri
* **Yakın Dükkanları Aynı Güne Toplama:** Kaydettiğiniz dükkan konumları sayesinde sistem, aynı sanayi sitesindeki veya birbirine yakın işletmeleri aynı güne gruplar; öğretmeni şehrin bir ucundan diğer ucuna boşuna koşturmaz.
* **Okul Günlerini Otomatik Ayıklama:** Öğrencinin `Şube` bilgisinden (*PZT-ÇRŞ*, *SALI* vb.) okulda olduğu günleri anlar ve öğrencinin okulda olduğu gün dükkana ziyaret yazmaz (elle taşırsanız da uyarı verir).
* **Otomatik Gün Önerisi:** Ayın tüm iş günlerini deneyerek en az çakışma ve en dengeli dağılımı sağlayan günleri sizin yerinize bulur.
* **İME Saatleri Modu:** 09:00–17:00 mesai penceresi ve 11:50–12:40 öğle dinlenmesini hesaba katar; işletme başı ziyaret süresine (örn. 40 dk) göre günlük kapasiteyi otomatik planlar.
* **Daha Önce Gidilen İşletmeler:** Planı ay ortasında yapıyorsanız, o ay zaten ziyaret ettiğiniz dükkanları **"Gidildi"** olarak işaretleyip plandan ve süre hesabından düşebilirsiniz.

### 🗂️ Bölge Kuralları Motoru
* Adreslerin içinde geçen anahtar kelimelere (`KADOSAN`, `DES`, `İMES`, `DUDULLU` vb.) göre işletmelerin bölgesini otomatik atar.
* **Adres Testi:** Kural eklemeden önce örnek bir adresi test kutusuna yazarak hangi kuralla eşleştiğini anında görebilirsiniz.
* **Kümeleme ( 🔗 ):** Henüz GPS koordinatı girilmemiş işletmelerde yakınlık hesabı yapılabilmesi için birbirine yakın bölgeleri aynı küme altında gruplayabilirsiniz.

### 📊 İstatistik ve Arşiv
* **İstatistik:** Öğrenci, tekil işletme, konumlu işletme oranı (%) ve bölge dağılımlarını grafiklerle sunar; tek A4 sayfasına sığdırarak yazdırır.
* **Arşiv:** Sözleşmesi feshedilen veya mezun olan öğrencileri silmek yerine arşive kaldırabilir, gerektiğinde tek tıkla geri alabilirsiniz.

---

## 🖨️ 4. Yazdırma ve Resmi Evrak Çıktıları

| Çıktı / Evrak Adı | Biçim | Açıklama |
| :--- | :--- | :--- |
| **Karekodlu (QR) Ziyaret Planı** | A4 Baskı / PDF | Her dükkanın yanında özel karekod bulunur. Telefon kamerasını okuttuğunuz an harita açılır ve sizi dükkanın kapısına götürür. Tek sayfaya otomatik sığdırılır. |
| **Görev Teslim Listesi** | Excel (`.xlsx`) | MEB standartlarına birebir uygun *"Koordinatör Öğretmen Görev Teslim Listesi"* şablonunu imza alanlarıyla birlikte tek tıkla Excel olarak indirir. |
| **İstatistik Raporu** | A4 Baskı / PDF | Alan, dal, bölge ve öğretmen bazlı öğrenci/işletme yükünü grafikli veya tablosal olarak tek sayfaya basar. |
| **Filtrelenmiş Ana Liste** | Excel & A4 Baskı | O an ekranda süzülmüş olan listeyi Excel'e aktarır veya A4 yatay sayfaya sığdırarak yazdırır. |

---

## 📥 5. Excel Yükleme Sütun Başlıkları

Excel'den veri yüklerken sütun sıralaması önemli değildir. Sistem aşağıdaki başlık isimlerini otomatik olarak tanır:

| Veri Alanı | Tanınan Excel Sütun Başlıkları (Herhangi Biri Olabilir) |
| :--- | :--- |
| **Öğrenci No** | `Öğr.No`, `Öğrenci No`, `Ogr.No`, `ogrNo`, `No`, `Numara` |
| **Ad Soyad** | `Ad Soyad`, `Adı Soyadı`, `Öğrenci Adı`, `İsim`, `adSoyad` |
| **İşletme Adı** | `Firma`, `Firma Adı`, `İşletme`, `İşletme Adı`, `Tespit Edilen Firma` |
| **İşyeri Adresi** | `Adres`, `İşyeri Adresi`, `İşletme Adresi`, `Temiz Adres` |
| **Öğretmen** | `Öğretmen`, `Koordinatör Öğretmen`, `ogretmen` |
| **Şube (Okul Günü)** | `Şube`, `Şubesi`, `Sube`, `sube` *(Örn: PZT, PZT-ÇRŞ, SALI)* |
| **Sınıf & Dal** | `Sınıf`, `Sınıfı` / `Dal`, `Dalı`, `Alan/Dal` |
| **İletişim & Usta** | `Öğrenci Tel`, `Telefon` / `İşyeri Tel`, `Firma Tel` / `Usta Öğretici`, `Usta` |
| **Konum & Not** | `Koordinat`, `Konum` / `Not`, `Notlar` |

---

## 💻 6. Kurulum ve Çalıştırma

Herhangi bir program, sunucu veya teknik kurulum **gerektirmez**:

1. Bu depodaki `index.html` dosyasını bilgisayarınıza veya telefonunuza indirin.
2. Dosyaya çift tıklayarak **Google Chrome, Microsoft Edge, Firefox veya Safari** tarayıcınızda açın.
3. Doğrudan kullanmaya başlayın!

> [!TIP]
> Excel okuma/yazma ve ikon kütüphaneleri internet üzerinden (CDN) yüklendiği için, dosyayı açarken cihazınızın internete bağlı olması önerilir.

---

## 🛠️ 7. Teknik Altyapı

* **Çekirdek:** Saf (Vanilla) JavaScript (ES6+), HTML5, CSS3 (Hiçbir framework bağımlılığı yoktur).
* **Kütüphaneler:**
  * [SheetJS (`xlsx.full.min.js`)](https://sheetjs.com/) — Excel okuma ve dışa aktarma.
  * [ExcelJS (`exceljs.min.js`)](https://github.com/exceljs/exceljs) — Resmi şablonlu Görev Teslim Listesi üretimi.
  * [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) — Çıktılar için vektörel (SVG) QR kod üretimi.
  * [Font Awesome 6](https://fontawesome.com/) — Arayüz ikon seti.

---

## 📄 Lisans

Bu proje eğitim kurumlarında, koordinatör öğretmenler ve okul idarecileri tarafından serbestçe kullanılabilir, paylaşılabilir ve geliştirilebilir.
