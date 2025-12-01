<template>
  <q-page>
    <!-- Hero Section -->
    <section class="hero-section relative-position overflow-hidden">
      <div class="hero-overlay"></div>
      
      <!-- Animated XAY Logos Background -->
      <div class="logo-background">
        <div v-for="i in 6" :key="i" class="floating-logo" :class="`logo-${i}`">
          <svg viewBox="0 0 200 120" xmlns="http://www.w3.org/2000/svg" class="logo-svg">
            <path d="M15,25 Q10,20 15,15 L25,5 Q30,0 35,5 L45,15 Q50,20 45,25 L40,30 L55,45 Q60,50 55,55 Q50,60 45,55 L30,40 L15,55 Q10,60 5,55 Q0,50 5,45 L20,30 L15,25 Z" 
                  fill="#C488D8" opacity="0.6"/>
            <path d="M70,15 Q75,5 85,5 Q95,5 100,15 L115,55 Q118,65 108,65 Q103,65 100,55 L98,45 L72,45 L70,55 Q67,65 57,65 Q47,65 50,55 L70,15 Z M75,35 L95,35 L85,15 Z" 
                  fill="#F9E475" opacity="0.6"/>
            <path d="M125,15 Q130,5 140,10 L155,30 L170,10 Q175,5 185,15 Q190,20 185,25 L165,50 L165,60 Q165,70 155,70 Q145,70 145,60 L145,50 L125,25 Q120,20 125,15 Z" 
                  fill="#87CEEB" opacity="0.6"/>
            <path d="M20,80 Q15,75 20,70 Q60,75 100,70 Q180,75 180,70 Q185,75 180,80 Q100,110 20,80 Z" 
                  fill="#C488D8" opacity="0.5"/>
          </svg>
        </div>
      </div>

      <div class="hero-content row items-center q-px-lg q-py-xl">
        <div class="col-12 col-md-7 q-pa-lg">
          <div class="hero-badge q-mb-md">
            <q-chip color="warning" text-color="dark" icon="auto_awesome" class="q-px-md">
              CE Sertifikalı | Güvenli Oyuncaklar
            </q-chip>
          </div>
          <h1 class="hero-title text-weight-bold text-white q-mb-md">
            Oyun, Öğrenme ve<br />
            <span class="text-gradient">Mutluluk</span>
          </h1>
          <p class="hero-subtitle text-h6 text-white q-mb-xl">
            Türkiye'nin en sevilen oyuncak markası | 2025 Yeni Katalog
          </p>
          <div class="row q-gutter-md">
            <q-btn
              to="/urunler"
              size="xl"
              rounded
              unelevated
              color="warning"
              text-color="dark"
              label="2025 Kataloğunu Gör"
              icon-right="arrow_forward"
              class="q-px-xl cta-button"
              no-caps
            />
            <q-btn
              to="/hakkimizda"
              size="xl"
              rounded
              outline
              color="white"
              label="Hakkımızda"
              class="q-px-xl cta-button-outline"
              no-caps
            />
          </div>
        </div>
        <div class="col-12 col-md-5 q-pa-lg hero-image-col">
          <div class="main-logo-display">
            <img src="xay-logo.png" alt="XAY Logo" class="hero-main-logo-img" />
          </div>
        </div>
      </div>
      
      <!-- Animated background shapes -->
      <div class="hero-shape shape-1"></div>
      <div class="hero-shape shape-2"></div>
      <div class="hero-shape shape-3"></div>
      <div class="hero-particles">
        <div v-for="i in 30" :key="i" class="particle" :style="getParticleStyle(i)"></div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features-section q-pa-xl">
      <div class="text-center q-mb-xl">
        <div class="section-badge q-mb-md">
          <q-chip color="primary" text-color="white" size="md" class="q-px-md">
            <q-icon name="star" class="q-mr-sm" />
            Özelliklerimiz
          </q-chip>
        </div>
        <h2 class="text-h3 text-weight-bold text-primary q-mb-md">Neden XAY?</h2>
        <p class="text-h6 text-grey-7">Oyuncaklarımızı özel kılan özellikler</p>
      </div>

      <div class="row q-col-gutter-xl justify-center">
        <div v-for="(feature, index) in features" :key="feature.title" class="col-12 col-sm-6 col-md-3">
          <q-card flat class="feature-card full-height text-center" :style="{ animationDelay: `${index * 0.1}s` }">
            <q-card-section class="q-pt-xl q-pb-lg">
              <div class="feature-icon-wrapper q-mb-lg">
                <q-icon :name="feature.icon" :color="feature.color" size="56px" />
              </div>
              <div class="text-h6 text-weight-bold q-mb-sm">{{ feature.title }}</div>
              <p class="text-grey-7 text-body2">{{ feature.description }}</p>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="stats-section bg-primary text-white q-pa-xl relative-position overflow-hidden">
      <!-- Background Logo Watermark -->
      <div class="stats-logo-bg">
        <svg viewBox="0 0 200 120" xmlns="http://www.w3.org/2000/svg">
          <path d="M15,25 Q10,20 15,15 L25,5 Q30,0 35,5 L45,15 Q50,20 45,25 L40,30 L55,45 Q60,50 55,55 Q50,60 45,55 L30,40 L15,55 Q10,60 5,55 Q0,50 5,45 L20,30 L15,25 Z" 
                fill="white" opacity="0.05"/>
          <path d="M70,15 Q75,5 85,5 Q95,5 100,15 L115,55 Q118,65 108,65 Q103,65 100,55 L98,45 L72,45 L70,55 Q67,65 57,65 Q47,65 50,55 L70,15 Z M75,35 L95,35 L85,15 Z" 
                fill="white" opacity="0.05"/>
          <path d="M125,15 Q130,5 140,10 L155,30 L170,10 Q175,5 185,15 Q190,20 185,25 L165,50 L165,60 Q165,70 155,70 Q145,70 145,60 L145,50 L125,25 Q120,20 125,15 Z" 
                fill="white" opacity="0.05"/>
          <path d="M20,80 Q15,75 20,70 Q60,75 100,70 Q180,75 180,70 Q185,75 180,80 Q100,110 20,80 Z" 
                fill="white" opacity="0.05"/>
        </svg>
      </div>
      <div class="row q-col-gutter-lg text-center relative-position" style="z-index: 2">
        <div v-for="stat in stats" :key="stat.label" class="col-12 col-sm-6 col-md-3">
          <div class="stat-card">
            <div class="text-h2 text-weight-bold text-xay-yellow stat-number">{{ stat.value }}</div>
            <div class="text-h6 q-mt-sm">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section q-pa-xl text-center">
      <div class="row justify-center">
        <div class="col-12 col-md-8">
          <h2 class="text-h3 text-weight-bold text-white q-mb-md">Bizimle İletişime Geçin</h2>
          <p class="text-h6 text-white q-mb-xl">Ürünlerimiz hakkında daha fazla bilgi almak ister misiniz?</p>
          <q-btn
            to="/iletisim"
            size="lg"
            rounded
            unelevated
            color="white"
            text-color="primary"
            label="İletişim"
            class="q-px-xl"
            no-caps
          />
        </div>
      </div>
    </section>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const getParticleStyle = () => {
  const size = Math.random() * 8 + 4
  return {
    width: `${size}px`,
    height: `${size}px`,
    left: `${Math.random() * 100}%`,
    top: `${Math.random() * 100}%`,
    animationDelay: `${Math.random() * 5}s`,
    animationDuration: `${Math.random() * 10 + 10}s`,
  }
}

const features = ref([
  {
    title: 'Güvenli',
    description: 'Tüm ürünlerimiz uluslararası güvenlik standartlarına uygundur',
    icon: 'verified',
    color: 'positive',
  },
  {
    title: 'Eğitici',
    description: 'Oyuncaklarımız çocukların gelişimine katkı sağlar',
    icon: 'school',
    color: 'info',
  },
  {
    title: 'Kaliteli',
    description: 'Dayanıklı malzemeler ile uzun ömürlü kullanım',
    icon: 'emoji_events',
    color: 'warning',
  },
  {
    title: 'Eğlenceli',
    description: 'Çocukların hayal gücünü harekete geçiren tasarımlar',
    icon: 'sentiment_very_satisfied',
    color: 'secondary',
  },
])

const stats = ref([
  { value: '15+', label: 'Yıllık Deneyim' },
  { value: '500+', label: 'Farklı Ürün' },
  { value: '50K+', label: 'Mutlu Çocuk' },
  { value: '100%', label: 'Müşteri Memnuniyeti' },
])
</script>

<style lang="scss" scoped>
// Hero Section - Modern Design
.hero-section {
  min-height: 90vh;
  background: linear-gradient(135deg, #8B5FA8 0%, #C488D8 50%, #F58F8F 100%);
  position: relative;
  padding-top: 80px;
  overflow: hidden;

  .hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: radial-gradient(circle at 20% 50%, rgba(135, 206, 235, 0.3), transparent 50%),
      radial-gradient(circle at 80% 80%, rgba(249, 228, 117, 0.2), transparent 50%),
      radial-gradient(circle at 50% 20%, rgba(196, 136, 216, 0.2), transparent 50%);
    z-index: 1;
  }

  .hero-content {
    position: relative;
    z-index: 3;
    min-height: 85vh;
    max-width: 1400px;
    margin: 0 auto;
  }
}

// Animated Logo Background
.logo-background {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 1;
  overflow: hidden;
}

.floating-logo {
  position: absolute;
  opacity: 0.15;
  filter: blur(2px);
  
  .logo-svg {
    width: 150px;
    height: auto;
    animation: rotateLogo 20s linear infinite;
  }

  &.logo-1 {
    top: 10%;
    left: 5%;
    animation: floatLogo1 25s ease-in-out infinite;
    .logo-svg {
      width: 180px;
    }
  }

  &.logo-2 {
    top: 60%;
    right: 10%;
    animation: floatLogo2 30s ease-in-out infinite;
    animation-delay: 2s;
    .logo-svg {
      width: 140px;
    }
  }

  &.logo-3 {
    bottom: 15%;
    left: 15%;
    animation: floatLogo3 28s ease-in-out infinite;
    animation-delay: 4s;
    .logo-svg {
      width: 160px;
    }
  }

  &.logo-4 {
    top: 30%;
    right: 20%;
    animation: floatLogo1 22s ease-in-out infinite;
    animation-delay: 1s;
    .logo-svg {
      width: 120px;
    }
  }

  &.logo-5 {
    bottom: 40%;
    left: 30%;
    animation: floatLogo2 26s ease-in-out infinite;
    animation-delay: 3s;
    .logo-svg {
      width: 170px;
    }
  }

  &.logo-6 {
    top: 50%;
    right: 5%;
    animation: floatLogo3 24s ease-in-out infinite;
    animation-delay: 5s;
    .logo-svg {
      width: 130px;
    }
  }
}

// Main Hero Logo Display
.main-logo-display {
  display: flex;
  align-items: center;
  justify-content: center;
  animation: fadeInScale 1.2s ease-out 0.5s both;
}

.hero-main-logo-img {
  width: 400px;
  height: auto;
  filter: drop-shadow(0 20px 60px rgba(0, 0, 0, 0.3));
  animation: gentleFloat 6s ease-in-out infinite, pulseGlow 3s ease-in-out infinite;

  @media (max-width: 768px) {
    width: 280px;
  }
}

.hero-badge {
  animation: slideDown 0.8s ease-out;
}

.hero-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  line-height: 1.2;
  animation: slideUp 0.8s ease-out 0.2s both;
  text-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}

.text-gradient {
  background: linear-gradient(135deg, $xay-yellow 0%, color-mix(in srgb, $xay-yellow 85%, white) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  filter: drop-shadow(0 0 30px rgba(249, 213, 110, 0.5));
}

.hero-subtitle {
  animation: slideUp 0.8s ease-out 0.4s both;
  opacity: 0.95;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

.cta-button {
  animation: slideUp 0.8s ease-out 0.6s both;
  box-shadow: 0 8px 30px rgba(249, 213, 110, 0.4);
  transition: all 0.3s ease;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 40px rgba(249, 213, 110, 0.6);
  }
}

.cta-button-outline {
  animation: slideUp 0.8s ease-out 0.7s both;
  border-width: 2px;
  transition: all 0.3s ease;

  &:hover {
    background: rgba(255, 255, 255, 0.1);
    transform: translateY(-4px);
  }
}

// Floating Toys Animation
.floating-toys {
  position: relative;
  height: 400px;
  animation: slideUp 0.8s ease-out 0.5s both;

  .toy-circle {
    position: absolute;
    width: 120px;
    height: 120px;
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(10px);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
    border: 2px solid rgba(255, 255, 255, 0.3);

    &.toy-1 {
      top: 50px;
      right: 100px;
      animation: floatToy 6s ease-in-out infinite;
    }

    &.toy-2 {
      bottom: 150px;
      right: 50px;
      animation: floatToy 8s ease-in-out infinite;
      animation-delay: 1s;
    }

    &.toy-3 {
      top: 200px;
      left: 50px;
      animation: floatToy 7s ease-in-out infinite;
      animation-delay: 2s;
    }
  }
}

// Background Particles
.hero-particles {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 1;

  .particle {
    position: absolute;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.6);
    animation: floatParticle linear infinite;
  }
}

.hero-shape {
  position: absolute;
  border-radius: 50%;
  opacity: 0.08;
  background: white;
  filter: blur(60px);
}

.shape-1 {
  width: 600px;
  height: 600px;
  top: -250px;
  right: -150px;
  animation: float 25s infinite ease-in-out;
}

.shape-2 {
  width: 400px;
  height: 400px;
  bottom: -150px;
  left: -100px;
  animation: float 20s infinite ease-in-out reverse;
}

.shape-3 {
  width: 300px;
  height: 300px;
  top: 40%;
  left: 5%;
  animation: float 30s infinite ease-in-out;
}

// Features Section
.features-section {
  background: linear-gradient(180deg, #fafafa 0%, #ffffff 100%);
}

.section-badge {
  animation: fadeIn 0.8s ease-out;
}

.feature-card {
  background: white;
  border-radius: 24px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  border: 1px solid rgba(123, 79, 160, 0.08);
  animation: fadeInUp 0.6s ease-out both;

  &:hover {
    transform: translateY(-12px) scale(1.02);
    box-shadow: 0 20px 40px rgba(123, 79, 160, 0.15);
    border-color: rgba(123, 79, 160, 0.2);

    .feature-icon-wrapper {
      transform: scale(1.1) rotate(5deg);
    }
  }
}

.feature-icon-wrapper {
  width: 100px;
  height: 100px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, rgba($primary, 0.08), rgba($secondary, 0.05));
  border-radius: 50%;
  transition: all 0.4s ease;
}

// Animations
@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes float {
  0%,
  100% {
    transform: translate(0, 0) rotate(0deg);
  }
  33% {
    transform: translate(-30px, -30px) rotate(5deg);
  }
  66% {
    transform: translate(30px, 20px) rotate(-5deg);
  }
}

@keyframes floatToy {
  0%,
  100% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-20px) rotate(10deg);
  }
}

@keyframes floatParticle {
  0% {
    transform: translateY(0) translateX(0);
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    transform: translateY(-100vh) translateX(50px);
    opacity: 0;
  }
}

@keyframes rotateLogo {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

@keyframes floatLogo1 {
  0%, 100% {
    transform: translate(0, 0) rotate(0deg) scale(1);
  }
  25% {
    transform: translate(30px, -40px) rotate(90deg) scale(1.1);
  }
  50% {
    transform: translate(-20px, -60px) rotate(180deg) scale(0.9);
  }
  75% {
    transform: translate(-40px, -30px) rotate(270deg) scale(1.05);
  }
}

@keyframes floatLogo2 {
  0%, 100% {
    transform: translate(0, 0) rotate(0deg) scale(1);
  }
  33% {
    transform: translate(-40px, 30px) rotate(120deg) scale(1.15);
  }
  66% {
    transform: translate(50px, -20px) rotate(240deg) scale(0.85);
  }
}

@keyframes floatLogo3 {
  0%, 100% {
    transform: translate(0, 0) rotate(0deg) scale(1);
  }
  20% {
    transform: translate(25px, 45px) rotate(72deg) scale(1.1);
  }
  40% {
    transform: translate(-35px, 20px) rotate(144deg) scale(0.95);
  }
  60% {
    transform: translate(15px, -40px) rotate(216deg) scale(1.08);
  }
  80% {
    transform: translate(-25px, -15px) rotate(288deg) scale(0.92);
  }
}

@keyframes gentleFloat {
  0%, 100% {
    transform: translateY(0px) rotate(0deg);
  }
  50% {
    transform: translateY(-20px) rotate(5deg);
  }
}

@keyframes pulseGlow {
  0%, 100% {
    filter: drop-shadow(0 20px 60px rgba(0, 0, 0, 0.3));
  }
  50% {
    filter: drop-shadow(0 25px 80px rgba(249, 228, 117, 0.6));
  }
}

@keyframes fadeInScale {
  0% {
    opacity: 0;
    transform: scale(0.8);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes slowRotate {
  0% {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  100% {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

.stats-section {
  background: linear-gradient(135deg, $primary 0%, color-mix(in srgb, $primary 90%, black) 100%);
  position: relative;
}

.stats-logo-bg {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 600px;
  height: auto;
  opacity: 0.8;
  animation: slowRotate 60s linear infinite;
  z-index: 1;

  svg {
    width: 100%;
    height: auto;
  }
}

.stat-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  padding: 2rem;
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.2);

  &:hover {
    transform: translateY(-8px);
    background: rgba(255, 255, 255, 0.15);
    box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
  }
}

.stat-number {
  text-shadow: 0 0 30px rgba(249, 228, 117, 0.8);
  animation: pulse 2s ease-in-out infinite;
}

.cta-section {
  background: linear-gradient(135deg, $accent 0%, color-mix(in srgb, $accent 90%, black) 100%);
}

// Custom color classes
.text-xay-yellow {
  color: $xay-yellow;
}

.bg-xay-yellow {
  background-color: $xay-yellow;
}
</style>
