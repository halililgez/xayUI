# XAY Oyuncak - Kurumsal Website

XAY Oyuncak firması için modern, renkli ve çocuk dostu bir kurumsal tanıtım websitesi.

## 🎨 Özellikler

- **Modern Tasarım**: Çocuklara hitap eden ama aynı zamanda kurumsal bir görünüm
- **Renk Paleti**: 2025 Tanıtım Kataloğu'ndan alınan renkler
  - Mor (#7B4FA0) - Ana marka rengi
  - Pembe/Kırmızı (#F58F8F) - İkincil renk
  - Turkuaz (#5DBFBE) - Vurgu rengi
  - Sarı (#F9D56E) - Özel vurgular
- **Responsive**: Mobil, tablet ve desktop için optimize edilmiş
- **4 Ana Sayfa**:
  - 🏠 Ana Sayfa - Hero section, özellikler, kategoriler
  - 🎁 Ürünler - Filtrelenebilir ürün galerisi
  - ℹ️ Hakkımızda - Firma hikayesi, değerler, timeline
  - 📧 İletişim - İletişim formu ve bilgiler

## 🚀 Kurulum

### Gereksinimler
- Node.js 20+
- npm 6+

### Proje Kurulumu

```bash
cd xay
npm install
```

### Development Sunucusu Başlatma

```bash
npm run dev
```

Tarayıcınızda otomatik olarak açılacaktır: http://localhost:9001/

### Production Build

```bash
npm run build
```

Build dosyaları `dist/spa` klasöründe oluşturulacaktır.

## 📁 Proje Yapısı

```
xay/
├── src/
│   ├── assets/          # Statik dosyalar (resimler, logolar)
│   ├── components/      # Yeniden kullanılabilir componentler
│   ├── layouts/         # Layout yapıları
│   │   └── MainLayout.vue
│   ├── pages/           # Sayfa componentleri
│   │   ├── IndexPage.vue      # Ana Sayfa
│   │   ├── ProductsPage.vue   # Ürünler
│   │   ├── AboutPage.vue      # Hakkımızda
│   │   └── ContactPage.vue    # İletişim
│   ├── router/          # Vue Router yapılandırması
│   ├── css/             # Global stil dosyaları
│   │   ├── app.scss
│   │   └── quasar.variables.scss  # Renk paleti
│   └── App.vue
├── public/              # Public assets
└── quasar.config.js     # Quasar yapılandırması
```

## 🎨 Renk Değişkenleri

Tüm renk değişkenleri `src/css/quasar.variables.scss` dosyasında tanımlanmıştır:

```scss
$primary: #7B4FA0;     // Mor
$secondary: #F58F8F;   // Pembe/Kırmızı
$accent: #5DBFBE;      // Turkuaz
$warning: #F9D56E;     // Sarı
```

## 🛠️ Teknolojiler

- **Vue 3** - Progressive JavaScript framework
- **Quasar Framework** - Vue.js tabanlı UI framework
- **Vue Router** - Routing için
- **Pinia** - State management
- **Vite** - Build tool
- **SCSS** - CSS preprocessor

## 📱 Responsive Tasarım

Website tüm ekran boyutları için optimize edilmiştir:
- 📱 Mobile: < 768px
- 📱 Tablet: 768px - 1024px
- 💻 Desktop: > 1024px

## 🎯 Sayfa Detayları

### Ana Sayfa (/)
- Hero section animasyonlu şekillerle
- "Neden XAY?" özellikleri
- İstatistikler bölümü
- Ürün kategorileri preview
- CTA (Call to Action) bölümü

### Ürünler (/urunler)
- Kategori, yaş grubu ve arama filtreleri
- 8 örnek ürün
- Detaylı ürün görüntüleme dialog'u
- Ürün kartları hover efektleri

### Hakkımızda (/hakkimizda)
- Firma hikayesi
- Misyon ve vizyon
- 6 temel değer
- Timeline (2010-2025)
- Sertifikalar
- Ekip katılım CTA

### İletişim (/iletisim)
- Detaylı iletişim formu
- KVKK onay checkbox'ı
- İletişim bilgileri kartları
- Harita alanı (placeholder)
- SSS (6 soru-cevap)
- Sosyal medya linkleri

## 🔄 Geliştirme Önerileri

1. **Logo Ekleme**: Logo dosyasını `src/assets/` klasörüne ekleyin ve `MainLayout.vue`'da XAY text'ini logo ile değiştirin
2. **Gerçek Ürün Verileri**: `ProductsPage.vue`'daki mock verileri API'dan çekin
3. **Google Maps**: `ContactPage.vue`'daki map placeholder'ı Google Maps ile değiştirin
4. **Form Backend**: İletişim formu için backend entegrasyonu ekleyin
5. **i18n**: Çoklu dil desteği için vue-i18n yapılandırması mevcuttur

## 📝 Lisans

© 2025 XAY Oyuncak. Tüm hakları saklıdır.

## 🤝 Katkıda Bulunma

Bu proje XAY Oyuncak için özel olarak geliştirilmiştir.

## 📞 Destek

Sorularınız için: info@xay.com.tr
