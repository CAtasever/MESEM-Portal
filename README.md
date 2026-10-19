# 🏢 MESEM Portal (v5.32)

> **Mesleki Eğitim Merkezleri (MESEM) için Koordinatör Öğretmen Ziyaret Planlama, İşletme Konum Yönetimi ve Görev Takip Portalı**

MESEM Portal; koordinatör öğretmenlerin işletmelerdeki çırak/kalfa öğrencilerini takip etmelerini, harita koordinatları üzerinden akıllı haftalık ziyaret rotaları oluşturmalarını, İME (İşletmelerde Mesleki Eğitim) saatlerini yönetmelerini ve resmi evrakları (Görev Teslim Listesi, QR Kodlu Ziyaret Çizelgesi) tek tıkla yazdırmalarını sağlayan **sunucusuz (serverless)**, tek sayfalık web uygulamasıdır.

---

## 📑 İçindekiler
- [Öne Çıkan Özellikler](#-öne-çıkan-özellikler)
- [Mimari ve Veri Güvenliği (Lokal Veri)](#-mimari-ve-veri-güvenliği-lokal-veri)
- [Kullanım Rehberi ve Modüller](#-kullanım-rehberi-ve-modüller)
  - [1. Liste ve Toplu İşlemler](#1-liste-ve-toplu-işlemler)
  - [2. İşletme Konum Modülü (Kritik)](#2-işletme-konum-modülü-kritik)
  - [3. Haftalık Planlama & İME Saatleri](#3-haftalık-planlama--ime-saatleri)
  - [4. Bölge Kuralları Motoru](#4-bölge-kuralları-motoru)
  - [5. İstatistik ve Grafikler](#5-istatistik-ve-grafikler)
  - [6. Arşiv Sistemi](#6-arşiv-sistemi)
- [Çıktılar ve Raporlama](#-çıktılar-ve-raporlama)
- [Hızlı Başlangıç / Kurulum](#-hızlı-başlangıç--kurulum)
- [Kullanılan Teknolojiler ve Kütüphaneler](#-kullanılan-teknolojiler-ve-kütüphaneler)
- [Lisans](#-lisans)

---

## 🌟 Öne Çıkan Özellikler

- **🔒 %100 Sunucusuz & Çevrimdışı (Offline-First):** Veriler uzak bir sunucuya veya buluta aktarılmaz; doğrudan tarayıcının yerel hafızasında (`localStorage`) saklanır.
- **📍 GPS ve Harita Entegrasyonu:** Sahada tek dokunuşla işletme koordinatı alma, Google Maps linklerini otomatik ayrıştırma.
- **🗺️ Akıllı Rota Algoritması:** Aynı bölgedeki/sanayi sitesindeki yakın işletmeleri tespit edip aynı güne gruplayarak öğretmenin yol süresini en aza indirir.
- **📅 Okul Günü Çakışma Önleme:** Öğrencilerin okulda olduğu günleri (`Şube` bilgisinden: *PZT-ÇRŞ* vb.) otomatik tanır ve o günlerde işletmeye ziyaret planlanmasını engeller.
- **📱 QR Kodlu A4 Çıktısı:** Ziyaret planındaki her işletmeye özel navigasyon QR kodu basılır; öğretmen telefon kamerasıyla okutarak kapıya kadar yol tarifi alır.
- **📊 Resmi Görev Teslim Listesi:** Millî Eğitim mevzuatına uygun formatta Excel formatında tek tıkla haftalık teslim çizelgesi üretir.
- **👥 Toplu Öğretmen Değişikliği:** Seçilen öğrencilerin koordinatör öğretmenini tek seferde değiştirme ve tek tıkla geri alma (`Undo`) desteği.

---

## 🛡️ Mimari ve Veri Güvenliği (Lokal Veri)

MESEM Portal, **KVKK ve veri mahremiyeti** standartlarını en üst düzeyde korumak amacıyla sunucusuz çalışacak şekilde tasarlanmıştır:

1. **İnternet/Üyelik İstemez:** Hiçbir kullanıcı adı, şifre veya veritabanı bağlantısı gerektirmez.
2. **Cihaza Özeldir:** Yüklenen veriler yalnızca o an kullanılan tarayıcı profiline özeldir.
3. **Yedek Alma Şartı:** Tarayıcı geçmişi veya önbelleği temizlendiğinde verilerin kaybolmaması için sistemde düzenli aralıklarla **"Yedek Al"** yapılması önerilir (Portal 7 günden eski yedeklerde kullanıcıyı uyarır).
4. **Cihazlar Arası Taşınabilirlik:** İndirilen `.json` yedek dosyası, **"Yedek Yükle"** düğmesiyle okul, ev veya cep telefonundaki tarayıcıya aktarılabilir.

---

## 📖 Kullanım Rehberi ve Modüller

### 1. Liste ve Toplu İşlemler
- **Excel Yükleme:** İdareden alınan standart e-MESEM listelerini (`.xlsx`, `.xls`) doğrudan tanır. Öğrenci numarası veya Id üzerinden mükerrer kayıtları engeller, var olanları günceller.
- **Çoklu Filtreleme:** Öğretmen, Bölge, Sınıf, Şube, Alan ve Dal bazında çoklu seçim (`Multi-select`) ile anında filtreleme.
- **Toplu Öğretmen Atama:** Tablodan seçilen onlarca öğrencinin koordinatörünü tek tıkla değiştirme ve yapılan hatayı **"Son değişikliği geri al"** butonuyla kurtarma imkânı.

### 2. İşletme Konum Modülü (Kritik)
İşletmelerin coğrafi konumlarının tek bir merkezden yönetildiği bölümdür:
- **Tekilleştirme:** Aynı işletmede çalışan birden fazla öğrenci varsa dükkan tek satırda görünür. Girilen koordinat, firmanın **tüm öğrencilerine otomatik yansır**.
- **GPS ile Yerinde Kayıt:** Sahada ziyaret esnasında **"Konumum"** butonuna basılarak telefonun GPS koordinatları (`41.0082, 28.9784`) birkaç saniye içinde işletmeye atanır.
- **Girdi Formatı Desteği:** İster enlem/boylam yazın, ister Google Maps bağlantısını yapıştırın; portal koordinatı otomatik ayıklar.
- **Hata Denetimi:** Türkiye sınırları dışına taşan veya çakışan koordinatları sarı ikazlarla uyarır.

### 3. Haftalık Planlama & İME Saatleri
- **Ay ve Gün Seçimi:** Ayın haftaları, çalışma günleri ve resmi tatiller hesaba katılarak ziyaret günleri belirlenir.
- **Otomatik Gün Önerisi:** En az okul günü çakışması yapacak gün kombinasyonunu matematiksel simülasyonla bulur.
- **İME Saatleri:** 09:00–17:00 mesai penceresi ve 11:50–12:40 öğle paydosu dikkate alınarak işletme başına ziyaret süresi (varsayılan 40 dk) üzerinden kapasite hesabı yapılır.
- **Gidilen İşletmeler:** Ay ortasında yapılan planlarda, o ay daha önce ziyaret edilmiş işletmeler işaretlenerek plandan çıkarılabilir.

### 4. Bölge Kuralları Motoru
- Adres metinleri içindeki anahtar kelimelere (`KADOSAN`, `DES`, `DUDULLU` vb.) göre adresleri otomatik bölgelere ayırır.
- Kurallar yukarıdan aşağıya öncelik sırasıyla çalışır; kullanıcı kural sırasını değiştirebilir veya adresi anında test edebilir.

### 5. İstatistik ve Grafikler
- Aktif öğrenci sayısı, tekil işletme sayısı ve konumlandırılmış işletme yüzdesi KPI kartlarında gösterilir.
- Alan, dal, öğretmen ve bölge dağılımları çubuk grafiklerle görselleştirilir; tek sayfaya sığdırılarak yazdırılabilir.

### 6. Arşiv Sistemi
- Ayrılan, mezun olan veya pasife alınan öğrencileri ana tablodan çıkarıp arşive taşır; istendiğinde tek tıkla geri yükler.

---

## 🖨️ Çıktılar ve Raporlama

| Çıktı Türü | Format | Açıklama |
| :--- | :--- | :--- |
| **Haftalık Ziyaret Planı** | Yazıcı / PDF | A4 Yatay/Dikey tek sayfaya otomatik ölçeklenen, dinamik QR kodlu ziyaret çizelgesi. |
| **Görev Teslim Listesi** | Excel (`.xlsx`) | Resmi MEB formatında, her haftası ayrı sayfada veya seçili hafta olarak üretilen imza teslim föyü. |
| **İstatistik Raporu** | Yazıcı / PDF | Alan, dal ve öğretmen dağılımlarını tek A4 sayfasına sığdıran özet rapor. |
| **Tam Sistem Yedeği** | JSON (`.json`) | Tüm veri, kural, tatil ve planları içeren taşınabilir veri paketi. |

---

## 🚀 Hızlı Başlangıç / Kurulum

Portalın çalışması için herhangi bir Node.js, Python veya sunucu ortamı kurmanıza **gerek yoktur**.

1. Depoyu klonlayın veya zip olarak indirin:
   ```bash
   git clone https://github.com/kullaniciadi/mesem-portal.git
