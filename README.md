# 🗺️ Türkiye Coğrafya Atlası & İl Bilmece Oyunu

**Türkiye Coğrafya Atlası**, Türkiye'nin coğrafi özelliklerini ve illerini interaktif bir şekilde harita üzerinde keşfetmeyi ve oyunlaştırılmış testlerle pekiştirmeyi sağlayan, KPSS ve genel kültür odaklı kapsamlı bir mobil uygulamadır.

> 🔒 **Kaynak Kod Bildirimi:** Bu projenin kaynak kodları, fikri mülkiyet ve ticari/özel sebeplerle gizli (private) tutulmaktadır. Bu depo (repository), bir portföy çalışması olarak projenin yeteneklerini, mimarisini ve gelişim sürecini sergilemek amacıyla oluşturulmuştur. Uygulamanın APK sürümüne aşağıdaki indirme bağlantısından ulaşabilirsiniz.

---

## 📱 Ekran Görüntüleri ve Video
<img width="2048" height="921" alt="WhatsApp Image 2026-07-14 at 23 03 46 (1)" src="https://github.com/user-attachments/assets/c86ed7e4-ddc8-4e06-9ebf-39e3ae687fe1" />
<img width="2048" height="921" alt="WhatsApp Image 2026-07-14 at 23 03 46 (3)" src="https://github.com/user-attachments/assets/39778edc-4266-4bd8-aa78-d1b746845b72" />
<img width="2048" height="921" alt="WhatsApp Image 2026-07-14 at 23 03 46 (5)" src="https://github.com/user-attachments/assets/53ce62a6-a0a4-4936-8d6c-9299d31c5a0d" />


---

## ✨ Temel Özellikler ve Modlar

Uygulama temel olarak **Serbest Keşif** ve **Oyun Modu** olmak üzere iki ana bölümden oluşur:

### 📍 Serbest Keşif Modu (İnteraktif Atlas)
*   **Dinamik Kategori Filtreleme:** Dağlar, Göller, Akarsular, Ovalar, Platolar, Deltalar, Barajlar ve Fay Hatları (KAF, DAF, BAF) gibi coğrafi oluşumların anlık olarak harita üzerinde açılıp kapatılabilmesi.
*   **Detaylı Fay Hatları:** Türkiye'nin ana fay hatlarının koordinat bazlı ve gerçeğe uygun şekilde harita üzerine çizilmesi.
*   **Akıllı Etiketleme:** Harita üzerindeki işaretçilerin ve etiketlerin üst üste binmesini önleyen (collision avoidance) özel hizalama algoritması.

### 🎮 Oyun Modu & İl Bilmece
*   **Coğrafi Konum Bulma:** Seçilen kategorilerdeki coğrafi oluşumların (örn: "Tuz Gölü nerede?", "Kızılırmak nereden doğar?") harita üzerindeki yerini tıklayarak tahmin etme.
*   **Gelişmiş Mesafe Hesaplama (Haversine):** Kullanıcının dokunduğu nokta ile hedefin gerçek koordinatları arasındaki sapma mesafesinin (km) anlık hesaplanarak dinamik puanlama yapılması.
*   **İl Sınırları Algılama:** İl bilmece oyununda, kullanıcının dokunduğu pikselin/koordinatın hedef ilin çokgen sınırları (polygon/path) içerisinde kalıp kalmadığının matematiksel tespiti.
*   **Senkronize Yüksek Skor (High Score):** Oyuncunun en yüksek skorunun `SharedPreferences` ile ön bellekten (pre-initialization) sıfır gecikmeyle yüklenip saklanması.
*   **Oyun İçi Analiz:** Oyun sonunda doğru/yanlış oranlarını, kategori bazlı başarıyı ve toplam puanı gösteren detaylı istatistik paneli.

---

## 🛠️ Kullanılan Teknolojiler ve Mimari

Bu proje geliştirilirken modern mobil geliştirme standartlarına ve performanslı kod yazımına özen gösterilmiştir:

*   **Framework:** Flutter
*   **Dil:** Dart
*   **State Management (Durum Yönetimi):** Riverpod *(Uygulama içi veri akışının, skorların ve harita filtrelerinin reaktif olarak yönetilmesi için kullanıldı.)*
*   **Veri Kalıcılığı:** SharedPreferences *(Skorların ve kullanıcı ayarlarının cihazda tutulması için asenkron gecikmeleri önleyen senkronize ön-yükleme (pre-init) mimarisi ile kuruldu.)*
*   **Grafik ve Çizim Motoru:** CustomPaint & Canvas API *(Türkiye haritasının render edilmesi, il sınırlarının çizilmesi ve dinamik fay hatlarının vektörel olarak oluşturulması.)*
*   **Matematiksel Hesaplamalar:** `dart:math` kütüphanesi kullanılarak küresel mesafe (Haversine formülü) ve çokgen içi nokta algılama (Point-in-Polygon) algoritmaları.

---

## 🧠 Bu Projeyi Geliştirirken Neler Öğrendim?

Bu uygulama benim için sadece bir ürün değil, aynı zamanda ciddi bir öğrenme ve problem çözme serüveni oldu. Bu süreçte özellikle şu konularda yetkinliğimi artırdım:

1.  **State Management (Riverpod) Ustalığı:** Global değişkenler yerine Riverpod ile birbirini dinleyen, asenkron verileri yönetebilen temiz bir state mimarisi kurmayı öğrendim.
2.  **CustomPaint ile İleri Seviye Vektörel Çizimler:** Flutter'ın hazır widget'larının dışına çıkarak, binlerce koordinattan oluşan Türkiye haritasını, il sınırlarını ve fay hatlarını `Canvas` üzerinde sıfırdan performanslı bir şekilde çizmeyi kavradım.
3.  **Matematiksel Algoritmalar Entegrasyonu:** Kullanıcının haritada tıkladığı x,y koordinatını enlem-boylam verisine dönüştürmeyi ve "Ray Casting" (noktanın çokgen içinde olup olmadığını bulma) ile Haversine (küresel iki nokta arası mesafe bulma) algoritmalarını mobil uygulamaya entegre etmeyi deneyimledim.
4.  **Performans Optimizasyonu:** Binlerce koordinat çizilirken FPS düşüşü yaşanmaması için çizimlerin nasıl optimize edilmesi gerektiğini öğrendim.
5.  **Kullanıcı Deneyimi (UI/UX):** Bilgi panellerinin, animasyonların ve renk paletlerinin kullanıcıyı yormadan bilgiyi nasıl aktarabileceği üzerine çalıştım.

---

## 📥 Uygulamayı İndir ve İncele

Uygulamanın Android versiyonunu (.apk) indirerek hemen deneyebilirsiniz:

👉 **[Uygulama APK Dosyasını İndir](https://github.com/shiver34/Haritalarla_KPSS_Showcase/releases/download/v1.0.0/app-release.apk)**


---

*Geliştirici:* **Abdullah Tuğra Zorbilmez**  
*İletişim:* [LinkedIn](https://www.linkedin.com/in/abdullah-tuğra-zorbilmez-70b4b0334) | [E-Posta](mailto:abdullah66tugra@gmail.com)
