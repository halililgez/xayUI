<template>
  <q-page>
    <!-- Hero Section -->
    <section class="about-hero text-center text-white q-pa-xl">
      <h1 class="text-h2 text-weight-bold q-mb-md">XAY Oyuncak Hakkında</h1>
      <p class="text-h6">Oyun, Öğrenme ve Mutluluk | 2010'dan beri</p>
    </section>

    <!-- Company Story -->
    <section class="q-pa-xl bg-white">
      <div class="row q-col-gutter-xl items-center">
        <div class="col-12 col-md-6">
          <q-img
            src="about-us.png"
            class="rounded-borders shadow-5"
          />
        </div>
        <div class="col-12 col-md-6">
          <h2 class="text-h3 text-weight-bold text-primary q-mb-md">XAY Hikayemiz</h2>
          <p class="text-body1 text-grey-8 q-mb-md">
            XAY Oyuncak, 2010 yılında oyuncak sektöründe fark yaratmak ve çocukların gelişimine katkı sağlamak 
            misyonuyla kuruldu. Kuruluşumuzdan bu yana amacımız, çocukların hayal gücünü ve yaratıcılığını 
            destekleyen, güvenli ve kaliteli oyuncaklar üreterek onların mutluluğuna ortak olmaktır.
          </p>
          <p class="text-body1 text-grey-8 q-mb-md">
            Üretimde kullandığımız tüm malzemeler CE sertifikalı ve uluslararası güvenlik standartlarına 
            uygun olarak seçilmektedir. Ahşap oyuncaklarımızda doğal ahşap, peluş ürünlerimizde hipoalerjenik 
            kumaşlar kullanarak çocuklarınızın sağlığını ön planda tutuyoruz.
          </p>
          <p class="text-body1 text-grey-8">
            Bugün 6 ana kategoride 500'ü aşkın ürünle, 0-12 yaş arası her yaş grubuna hitap eden oyuncaklar 
            üretiyoruz. Türkiye genelinde binlerce satış noktasında bulunan ürünlerimizle, milyonlarca çocuğun 
            gülümsemesine vesile oluyoruz.
          </p>
        </div>
      </div>
    </section>

    <!-- Mission & Vision -->
    <section class="q-pa-xl bg-grey-2">
      <div class="row q-col-gutter-lg">
        <div class="col-12 col-md-6">
          <q-card flat bordered class="full-height q-pa-lg mission-card">
            <div class="row items-center q-mb-md">
              <q-icon name="flag" size="48px" color="primary" class="q-mr-md" />
              <h3 class="text-h4 text-weight-bold">Misyonumuz</h3>
            </div>
            <p class="text-body1 text-grey-8">
              Her çocuğun mutlu, sağlıklı ve güvenli oyuncaklarla büyümesini sağlamak. Eğitici, yaratıcı ve 
              gelişim odaklı oyuncaklar üreterek çocukların motor, bilişsel ve sosyal becerilerini desteklemek. 
              Aile ile çocuk arasındaki bağı güçlendirecek, kaliteli zaman geçirmelerini sağlayacak oyuncaklar 
              tasarlamaktır.
            </p>
          </q-card>
        </div>

        <div class="col-12 col-md-6">
          <q-card flat bordered class="full-height q-pa-lg vision-card">
            <div class="row items-center q-mb-md">
              <q-icon name="visibility" size="48px" color="accent" class="q-mr-md" />
              <h3 class="text-h4 text-weight-bold">Vizyonumuz</h3>
            </div>
            <p class="text-body1 text-grey-8">
              Türkiye'nin ve dünya çapında tanınan, çocukların en sevdiği ve ailelerin en çok güvendiği oyuncak 
              markası olmak. Sürdürülebilir, çevre dostu üretim anlayışıyla sektöre öncülük ederek, geleceğin 
              oyuncak dünyasını şekillendirmek. İnovasyon ve kalitede sınırları zorlamak, her çocuğun hayal 
              dünyasına ilham vermektir.
            </p>
          </q-card>
        </div>
      </div>
    </section>

    <!-- Values -->
    <section class="q-pa-xl bg-white">
      <div class="text-center q-mb-xl">
        <h2 class="text-h3 text-weight-bold text-primary q-mb-md">Değerlerimiz</h2>
        <p class="text-h6 text-grey-7">Bizi biz yapan ilkeler</p>
      </div>

      <div class="row q-col-gutter-lg">
        <div v-for="value in values" :key="value.title" class="col-12 col-sm-6 col-md-4">
          <q-card flat bordered class="value-card text-center full-height q-pa-lg">
            <q-icon :name="value.icon" :color="value.color" size="64px" class="q-mb-md" />
            <h4 class="text-h6 text-weight-bold q-mb-sm">{{ value.title }}</h4>
            <p class="text-body2 text-grey-7">{{ value.description }}</p>
          </q-card>
        </div>
      </div>
    </section>

    <!-- Timeline -->
    <section class="q-pa-xl bg-grey-2">
      <div class="text-center q-mb-xl">
        <h2 class="text-h3 text-weight-bold text-primary q-mb-md">Yolculuğumuz</h2>
        <p class="text-h6 text-grey-7">Dönüm noktalarımız</p>
      </div>

      <div class="timeline-container">
        <div v-for="(milestone, index) in timeline" :key="index" class="timeline-item" :class="{ reverse: index % 2 }">
          <q-card flat bordered class="timeline-card q-pa-lg">
            <div class="text-h4 text-weight-bold text-primary q-mb-sm">{{ milestone.year }}</div>
            <h5 class="text-h6 text-weight-bold q-mb-sm">{{ milestone.title }}</h5>
            <p class="text-body2 text-grey-8">{{ milestone.description }}</p>
          </q-card>
        </div>
      </div>
    </section>

    <!-- Certifications -->
    <section class="q-pa-xl bg-white text-center">
      <h2 class="text-h3 text-weight-bold text-primary q-mb-md">Sertifikalarımız</h2>
      <p class="text-h6 text-grey-7 q-mb-xl">Kalite ve güvenlik taahhüdümüz</p>

      <div class="row q-col-gutter-lg justify-center">
        <div v-for="cert in certifications" :key="cert.name" class="col-6 col-sm-4 col-md-2">
          <q-card flat bordered class="cert-card q-pa-md cursor-pointer">
            <q-icon :name="cert.icon" size="64px" :color="cert.color" class="q-mb-sm" />
            <div class="text-caption text-weight-bold">{{ cert.name }}</div>
          </q-card>
        </div>
      </div>
    </section>

    <!-- Team CTA -->
    <section class="team-cta q-pa-xl text-center text-white">
      <h2 class="text-h3 text-weight-bold q-mb-md">Ekibimize Katılın</h2>
      <p class="text-h6 q-mb-xl">XAY ailesi olmak ister misiniz?</p>
      <q-btn
        to="/iletisim"
        size="lg"
        rounded
        unelevated
        color="white"
        text-color="primary"
        label="Bize Ulaşın"
        class="q-px-xl"
        no-caps
      />
    </section>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const values = ref([
  {
    title: 'Güvenlik',
    description: 'Çocukların güvenliği her zaman önceliğimizdir. Tüm ürünlerimiz uluslararası standartlara uygundur.',
    icon: 'shield',
    color: 'positive',
  },
  {
    title: 'Kalite',
    description: 'En iyi malzemeler ve titiz üretim süreçleriyle dayanıklı ürünler sunuyoruz.',
    icon: 'star',
    color: 'warning',
  },
  {
    title: 'İnovasyon',
    description: 'Sürekli araştırma ve geliştirme ile çağın gereksinimlerine uygun oyuncaklar tasarlıyoruz.',
    icon: 'lightbulb',
    color: 'info',
  },
  {
    title: 'Sürdürülebilirlik',
    description: 'Çevre dostu malzemeler kullanarak geleceğe saygılı üretim yapıyoruz.',
    icon: 'eco',
    color: 'accent',
  },
  {
    title: 'Eğitim',
    description: 'Oyuncaklarımız eğlence ile öğrenmeyi birleştirerek çocukların gelişimine katkı sağlar.',
    icon: 'school',
    color: 'primary',
  },
  {
    title: 'Müşteri Odaklılık',
    description: 'Müşterilerimizin memnuniyeti bizim başarımızdır. Her zaman yanınızdayız.',
    icon: 'favorite',
    color: 'secondary',
  },
])

const timeline = ref([
  {
    year: '2010',
    title: 'Kuruluş',
    description: 'XAY Oyuncak, çocukların dünyasını renklendirme vizyonuyla kuruldu.',
  },
  {
    year: '2012',
    title: 'İlk Ödül',
    description: 'En İyi Eğitici Oyuncak Tasarımı kategorisinde ödül kazandık.',
  },
  {
    year: '2015',
    title: 'Yeni Tesis',
    description: '10.000 m² modern üretim tesisimizi açtık ve kapasitemizi 3 katına çıkardık.',
  },
  {
    year: '2018',
    title: 'Uluslararası Açılım',
    description: 'Ürünlerimiz 15 farklı ülkeye ihraç edilmeye başlandı.',
  },
  {
    year: '2021',
    title: 'Dijital Dönüşüm',
    description: 'AR destekli oyuncak serimizle dijital dünyaya adım attık.',
  },
  {
    year: '2025',
    title: '500+ Ürün',
    description: 'Ürün portföyümüz 500 çeşidi aştı ve lider marka olduk.',
  },
])

const certifications = ref([
  { name: 'CE', icon: 'verified_user', color: 'positive' },
  { name: 'ISO 9001', icon: 'assured_workload', color: 'primary' },
  { name: 'EN 71', icon: 'security', color: 'info' },
  { name: 'ASTM', icon: 'workspace_premium', color: 'accent' },
  { name: 'Eco-Friendly', icon: 'eco', color: 'positive' },
  { name: 'TSE', icon: 'verified', color: 'warning' },
])
</script>

<style lang="scss" scoped>
.about-hero {
  background: linear-gradient(135deg, $primary 0%, color-mix(in srgb, $primary 90%, black) 100%);
  min-height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.mission-card,
.vision-card,
.value-card {
  border-radius: 16px;
  transition: all 0.3s ease;

  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  }
}

.timeline-container {
  max-width: 800px;
  margin: 0 auto;
  position: relative;

  &::before {
    content: '';
    position: absolute;
    width: 4px;
    background: $primary;
    top: 0;
    bottom: 0;
    left: 50%;
    margin-left: -2px;

    @media (max-width: 768px) {
      left: 30px;
    }
  }
}

.timeline-item {
  position: relative;
  width: 50%;
  padding: 20px 40px;
  box-sizing: border-box;

  @media (max-width: 768px) {
    width: 100%;
    padding-left: 80px;
  }

  &::after {
    content: '';
    position: absolute;
    width: 20px;
    height: 20px;
    background: white;
    border: 4px solid $primary;
    top: 30px;
    border-radius: 50%;
    z-index: 1;
  }

  &:not(.reverse) {
    left: 0;

    &::after {
      right: -10px;

      @media (max-width: 768px) {
        left: 20px;
      }
    }
  }

  &.reverse {
    left: 50%;

    @media (max-width: 768px) {
      left: 0;
    }

    &::after {
      left: -10px;

      @media (max-width: 768px) {
        left: 20px;
      }
    }
  }
}

.timeline-card {
  border-radius: 16px;
}

.cert-card {
  border-radius: 12px;
  transition: all 0.3s ease;

  &:hover {
    transform: scale(1.1);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  }
}

.team-cta {
  background: linear-gradient(135deg, $secondary 0%, color-mix(in srgb, $secondary 90%, black) 100%);
}
</style>
