<template>
  <q-layout view="hHh lpR fff">
    <q-header class="modern-header" :class="{ 'header-scrolled': scrolled }">
      <q-toolbar class="q-px-lg" style="min-height: 80px">
        <!-- Logo -->
        <q-toolbar-title class="row items-center cursor-pointer q-ml-md" @click="$router.push('/')">
          <img src="~assets/../public/xay-logo.png" alt="XAY Logo" class="xay-logo-img" />
        </q-toolbar-title>

        <!-- Desktop Menu -->
        <div v-if="$q.screen.gt.sm" class="row q-gutter-md items-center">
          <router-link
            v-for="link in navLinks"
            :key="link.path"
            :to="link.path"
            class="nav-link text-weight-medium"
            :class="{ 'nav-link-active': $route.path === link.path }"
          >
            {{ link.label }}
          </router-link>
        </div>

        <!-- Mobile Menu Button -->
        <q-btn
          v-if="$q.screen.lt.md"
          flat
          dense
          round
          icon="menu"
          class="mobile-menu-btn"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
      </q-toolbar>
    </q-header>

    <!-- Mobile Drawer -->
    <q-drawer v-model="leftDrawerOpen" :width="280" bordered class="modern-drawer">
      <div class="drawer-header q-pa-lg">
        <div class="xay-logo-svg-drawer">
          <svg viewBox="0 0 200 120" xmlns="http://www.w3.org/2000/svg">
            <path d="M15,25 Q10,20 15,15 L25,5 Q30,0 35,5 L45,15 Q50,20 45,25 L40,30 L55,45 Q60,50 55,55 Q50,60 45,55 L30,40 L15,55 Q10,60 5,55 Q0,50 5,45 L20,30 L15,25 Z" 
                  fill="#C488D8" stroke="#9B6BB0" stroke-width="1.5"/>
            <path d="M70,15 Q75,5 85,5 Q95,5 100,15 L115,55 Q118,65 108,65 Q103,65 100,55 L98,45 L72,45 L70,55 Q67,65 57,65 Q47,65 50,55 L70,15 Z M75,35 L95,35 L85,15 Z" 
                  fill="#F9E475" stroke="#E5C842" stroke-width="1.5"/>
            <path d="M125,15 Q130,5 140,10 L155,30 L170,10 Q175,5 185,15 Q190,20 185,25 L165,50 L165,60 Q165,70 155,70 Q145,70 145,60 L145,50 L125,25 Q120,20 125,15 Z" 
                  fill="#87CEEB" stroke="#5BA8C8" stroke-width="1.5"/>
            <path d="M20,80 Q15,75 20,70 Q60,75 100,70 Q180,75 180,70 Q185,75 180,80 Q100,110 20,80 Z" 
                  fill="#C488D8" stroke="#9B6BB0" stroke-width="2" fill-opacity="0.8"/>
          </svg>
        </div>
        <div class="text-h5 text-weight-bold text-primary q-mt-sm">XAY</div>
      </div>

      <q-list class="q-px-md">
        <q-item
          v-for="link in navLinks"
          :key="link.path"
          clickable
          v-ripple
          :to="link.path"
          exact
          class="drawer-item rounded-borders q-mb-xs"
          @click="leftDrawerOpen = false"
        >
          <q-item-section avatar>
            <q-icon :name="link.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label class="text-weight-medium">{{ link.label }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-dark text-white footer-compact">
      <div class="footer-content q-px-lg q-py-md">
        <div class="row items-center justify-between">
          <!-- Logo & Description -->
          <div class="col-12 col-md-4 q-mb-sm">
            <div class="text-h6 text-weight-bold">XAY</div>
            <p class="text-caption q-ma-none text-grey-5">Oyuncak dünyasında hayal gücünü gerçeğe dönüştüren lider marka</p>
          </div>

          <!-- Quick Links -->
          <div class="col-12 col-md-4 q-mb-sm text-center">
            <div class="row inline q-gutter-sm justify-center">
              <router-link to="/" class="footer-link">Ana Sayfa</router-link>
              <span class="text-grey-6">|</span>
              <router-link to="/urunler" class="footer-link">Ürünler</router-link>
              <span class="text-grey-6">|</span>
              <router-link to="/hakkimizda" class="footer-link">Hakkımızda</router-link>
              <span class="text-grey-6">|</span>
              <router-link to="/iletisim" class="footer-link">İletişim</router-link>
            </div>
          </div>

          <!-- Contact Info -->
          <div class="col-12 col-md-4 q-mb-sm text-right">
            <div class="text-caption">
              <div class="q-mb-xs">
                <q-icon name="mail" size="14px" class="q-mr-xs" />
                info@xay.com.tr
              </div>
              <div>
                <q-icon name="phone" size="14px" class="q-mr-xs" />
                +90 (xxx) xxx xx xx
              </div>
            </div>
          </div>
        </div>

        <!-- Copyright -->
        <q-separator class="q-my-sm" color="grey-8" />
        <div class="text-center text-caption text-grey-5">
          © 2025 XAY Oyuncak. Tüm hakları saklıdır.
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const leftDrawerOpen = ref(false)
const scrolled = ref(false)

const navLinks = [
  { path: '/', label: 'Ana Sayfa', icon: 'home' },
  { path: '/urunler', label: 'Ürünler', icon: 'toys' },
  { path: '/hakkimizda', label: 'Hakkımızda', icon: 'info' },
  { path: '/iletisim', label: 'İletişim', icon: 'mail' },
]

const handleScroll = () => {
  scrolled.value = window.scrollY > 20
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style lang="scss" scoped>
// Modern Header
.modern-header {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(123, 79, 160, 0.1);
  transition: all 0.3s ease;
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.05);

  &.header-scrolled {
    background: rgba(255, 255, 255, 0.98);
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.08);
  }
}

// Logo Container
.xay-logo-container {
  transition: transform 0.3s ease;

  &:hover {
    transform: scale(1.05);
  }
}

.xay-logo-img {
  height: 60px;
  width: auto;
  transition: transform 0.3s ease;

  &:hover {
    transform: scale(1.05);
  }
}

.xay-logo-text {
  font-family: 'Arial Rounded MT Bold', 'Helvetica Rounded', Arial, sans-serif;
  letter-spacing: 3px;
  color: $primary;
  background: linear-gradient(135deg, $primary 0%, $secondary 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

// Navigation Links
.nav-link {
  position: relative;
  color: #2c3e50;
  text-decoration: none;
  font-size: 0.95rem;
  padding: 8px 16px;
  border-radius: 8px;
  transition: all 0.3s ease;

  &::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    width: 0;
    height: 2px;
    background: linear-gradient(90deg, $primary, $secondary);
    transform: translateX(-50%);
    transition: width 0.3s ease;
  }

  &:hover {
    color: $primary;
    background: rgba($primary, 0.05);

    &::before {
      width: 80%;
    }
  }

  &.nav-link-active {
    color: $primary;
    font-weight: 600;

    &::before {
      width: 80%;
    }
  }
}

.mobile-menu-btn {
  color: $primary;
  background: rgba($primary, 0.1);

  &:hover {
    background: rgba($primary, 0.2);
  }
}

// Modern Drawer
.modern-drawer {
  background: linear-gradient(180deg, rgba($primary, 0.03) 0%, rgba(255, 255, 255, 1) 100%);
}

.drawer-header {
  background: linear-gradient(135deg, rgba($primary, 0.1) 0%, rgba($secondary, 0.05) 100%);
  border-bottom: 1px solid rgba($primary, 0.1);
}

.xay-logo-svg-drawer {
  width: 80px;
  height: 60px;
  color: $primary;
}

.drawer-item {
  transition: all 0.3s ease;
  margin-bottom: 4px;

  &:hover {
    background: rgba($primary, 0.08);
    transform: translateX(8px);
  }

  &.q-router-link--active {
    background: linear-gradient(90deg, rgba($primary, 0.15), rgba($secondary, 0.1));
    color: $primary;
    font-weight: 600;
  }
}

// Footer
.footer-compact {
  .footer-content {
    max-width: 1400px;
    margin: 0 auto;
  }
}

.footer-link {
  color: white;
  text-decoration: none;
  font-size: 0.875rem;
  transition: all 0.3s ease;

  &:hover {
    color: $warning;
    transform: translateY(-2px);
  }
}
</style>
