<template>
  <q-page class="products-page">
    <!-- Page Header -->
    <div class="page-header text-center q-pa-xl">
      <div class="container">
        <q-chip color="warning" text-color="dark" size="lg" class="q-mb-md">
          <q-icon name="menu_book" class="q-mr-sm" />
          2025 Katalog
        </q-chip>
        <h1 class="text-h2 text-weight-bold text-white q-mb-md">XAY Ürün Kataloğu</h1>
        <p class="text-h6 text-white">CE Sertifikalı, güvenli ve eğlenceli oyuncaklar</p>
      </div>
    </div>

    <!-- Category Showcase -->
    <section class="categories-section q-pa-xl">
      <div class="container">
        <h2 class="text-h4 text-weight-bold text-center q-mb-xl">Kategoriler</h2>
        <div class="row q-col-gutter-md">
          <div
            v-for="category in productCategories"
            :key="category.id"
            class="col-12 col-sm-6 col-md-4 col-lg-2"
          >
            <q-card
              flat
              bordered
              class="category-card cursor-pointer"
              :class="{ active: selectedCategory === category.slug }"
              @click="selectedCategory = selectedCategory === category.slug ? 'all' : category.slug"
            >
              <q-card-section class="text-center">
                <q-icon :name="category.icon" size="48px" :color="category.color" />
                <div class="text-subtitle2 text-weight-bold q-mt-sm">{{ category.name }}</div>
                <div class="text-caption text-grey-7">{{ category.description }}</div>
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
    </section>

    <!-- Filters -->
    <section class="filters-section q-pa-md bg-grey-2">
      <div class="container">
        <div class="row q-col-gutter-md items-center">
          <div class="col-12 col-md-4">
            <q-select
              v-model="selectedCategory"
              :options="categoryOptions"
              label="Kategori"
              outlined
              dense
              emit-value
              map-options
              bg-color="white"
            >
              <template v-slot:prepend>
                <q-icon name="category" />
              </template>
            </q-select>
          </div>
          <div class="col-12 col-md-4">
            <q-select
              v-model="selectedAgeGroup"
              :options="ageGroupOptions"
              label="Yaş Grubu"
              outlined
              dense
              emit-value
              map-options
              bg-color="white"
            >
              <template v-slot:prepend>
                <q-icon name="child_care" />
              </template>
            </q-select>
          </div>
          <div class="col-12 col-md-4">
            <q-input v-model="searchQuery" label="Ürün Ara" outlined dense bg-color="white">
              <template v-slot:prepend>
                <q-icon name="search" />
              </template>
              <template v-slot:append v-if="searchQuery">
                <q-icon name="close" class="cursor-pointer" @click="searchQuery = ''" />
              </template>
            </q-input>
          </div>
        </div>
        <div class="q-mt-md text-center text-grey-7">
          {{ filteredProducts.length }} ürün bulundu
        </div>
      </div>
    </section>

    <!-- Products Grid -->
    <section class="products-section q-pa-xl">
      <div class="container">
        <div class="row q-col-gutter-lg">
          <div
            v-for="product in filteredProducts"
            :key="product.id"
            class="col-12 col-sm-6 col-md-4 col-lg-3"
          >
            <q-card
              flat
              bordered
              class="product-card full-height cursor-pointer"
              @click="showProductDetail(product)"
            >
              <div class="product-image-wrapper relative-position">
                <q-img :src="product.image" ratio="1" class="product-image" />
                <div class="product-badges">
                  <q-badge v-if="product.isNew" color="accent" class="q-pa-sm">
                    <q-icon name="fiber_new" size="xs" class="q-mr-xs" />
                    Yeni
                  </q-badge>
                  <q-badge v-if="product.isBestseller" color="warning" text-color="dark" class="q-pa-sm">
                    <q-icon name="star" size="xs" class="q-mr-xs" />
                    Çok Satan
                  </q-badge>
                </div>
              </div>

              <q-card-section>
                <div class="text-overline text-grey-7">{{ product.id }}</div>
                <div class="text-h6 text-weight-bold q-mb-sm ellipsis-2-lines">{{ product.name }}</div>
                <div class="text-body2 text-grey-7 q-mb-md ellipsis-2-lines">
                  {{ product.description }}
                </div>

                <div class="row items-center q-mb-sm">
                  <q-chip size="sm" :color="getAgeChipColor(product.ageGroup)" text-color="white" dense>
                    {{ getAgeLabel(product.ageGroup) }}
                  </q-chip>
                  <q-chip
                    size="sm"
                    :color="getCategoryInfo(product.category)?.color"
                    text-color="white"
                    dense
                  >
                    <q-icon :name="getCategoryInfo(product.category)?.icon" size="xs" class="q-mr-xs" />
                    {{ getCategoryInfo(product.category)?.name }}
                  </q-chip>
                </div>

                <div class="text-h5 text-primary text-weight-bold">₺{{ product.price }}</div>
              </q-card-section>

              <q-separator />

              <q-card-actions>
                <q-btn flat color="primary" label="Detayları Gör" icon-right="arrow_forward" class="full-width" />
              </q-card-actions>
            </q-card>
          </div>
        </div>

        <div v-if="filteredProducts.length === 0" class="text-center q-pa-xl">
          <q-icon name="search_off" size="80px" color="grey-5" />
          <p class="text-h6 text-grey-7 q-mt-md">Aradığınız kriterlere uygun ürün bulunamadı</p>
          <q-btn
            label="Filtreleri Temizle"
            color="primary"
            outline
            @click="clearFilters"
            class="q-mt-md"
          />
        </div>
      </div>
    </section>

    <!-- Product Detail Dialog -->
    <q-dialog v-model="showDialog" maximized transition-show="slide-up" transition-hide="slide-down">
      <q-card v-if="selectedProduct" class="product-detail-card">
        <q-bar class="bg-primary text-white">
          <q-space />
          <q-btn dense flat icon="close" v-close-popup>
            <q-tooltip>Kapat</q-tooltip>
          </q-btn>
        </q-bar>

        <q-card-section class="q-pa-xl">
          <div class="row q-col-gutter-xl">
            <div class="col-12 col-md-6">
              <q-img :src="selectedProduct.image" ratio="1" class="product-detail-image rounded-borders" />
              <div class="q-mt-md row q-gutter-sm">
                <q-badge v-if="selectedProduct.isNew" color="accent" class="q-pa-md">
                  <q-icon name="fiber_new" size="sm" class="q-mr-sm" />
                  Yeni Ürün
                </q-badge>
                <q-badge v-if="selectedProduct.isBestseller" color="warning" text-color="dark" class="q-pa-md">
                  <q-icon name="star" size="sm" class="q-mr-sm" />
                  Çok Satan Ürün
                </q-badge>
              </div>
            </div>

            <div class="col-12 col-md-6">
              <div class="text-overline text-grey-7">{{ selectedProduct.id }}</div>
              <h2 class="text-h3 text-weight-bold q-mb-md">{{ selectedProduct.name }}</h2>
              
              <div class="q-mb-lg">
                <q-chip :color="getAgeChipColor(selectedProduct.ageGroup)" text-color="white" size="lg">
                  <q-icon name="child_care" class="q-mr-sm" />
                  {{ getAgeLabel(selectedProduct.ageGroup) }}
                </q-chip>
                <q-chip
                  :color="getCategoryInfo(selectedProduct.category)?.color"
                  text-color="white"
                  size="lg"
                >
                  <q-icon :name="getCategoryInfo(selectedProduct.category)?.icon" class="q-mr-sm" />
                  {{ getCategoryInfo(selectedProduct.category)?.name }}
                </q-chip>
              </div>

              <div class="text-h4 text-primary text-weight-bold q-mb-xl">₺{{ selectedProduct.price }}</div>

              <div class="q-mb-xl">
                <h3 class="text-h6 text-weight-bold q-mb-md">
                  <q-icon name="description" class="q-mr-sm" />
                  Ürün Açıklaması
                </h3>
                <p class="text-body1 text-grey-8">{{ selectedProduct.description }}</p>
              </div>

              <div class="q-mb-xl">
                <h3 class="text-h6 text-weight-bold q-mb-md">
                  <q-icon name="verified" class="q-mr-sm" />
                  Özellikler
                </h3>
                <q-list bordered separator class="rounded-borders">
                  <q-item v-for="(feature, index) in selectedProduct.features" :key="index">
                    <q-item-section avatar>
                      <q-icon name="check_circle" color="positive" />
                    </q-item-section>
                    <q-item-section>
                      <q-item-label class="text-body1">{{ feature }}</q-item-label>
                    </q-item-section>
                  </q-item>
                </q-list>
              </div>

              <div class="row q-gutter-md">
                <q-btn
                  unelevated
                  rounded
                  size="lg"
                  color="primary"
                  label="İletişime Geç"
                  icon="phone"
                  to="/iletisim"
                  class="q-px-xl"
                  no-caps
                />
                <q-btn
                  outline
                  rounded
                  size="lg"
                  color="primary"
                  label="Tüm Ürünler"
                  icon="grid_view"
                  v-close-popup
                  class="q-px-xl"
                  no-caps
                />
              </div>
            </div>
          </div>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup>
import { ref, computed } from 'vue'
import { productCategories, ageGroups, catalogProducts } from 'src/data/catalogData.js'

const selectedCategory = ref('all')
const selectedAgeGroup = ref('all')
const searchQuery = ref('')
const selectedProduct = ref(null)
const showDialog = ref(false)

const categoryOptions = computed(() => [
  { label: 'Tüm Kategoriler', value: 'all' },
  ...productCategories.map((cat) => ({
    label: cat.name,
    value: cat.slug,
  })),
])

const ageGroupOptions = computed(() => [
  { label: 'Tüm Yaş Grupları', value: 'all' },
  ...ageGroups.map((age) => ({
    label: age.label,
    value: age.value,
  })),
])

const filteredProducts = computed(() => {
  return catalogProducts.filter((product) => {
    const matchesCategory = selectedCategory.value === 'all' || product.category === selectedCategory.value
    const matchesAgeGroup = selectedAgeGroup.value === 'all' || product.ageGroup === selectedAgeGroup.value
    const matchesSearch =
      searchQuery.value === '' ||
      product.name.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      product.description.toLowerCase().includes(searchQuery.value.toLowerCase())

    return matchesCategory && matchesAgeGroup && matchesSearch
  })
})

function getCategoryInfo(slug) {
  return productCategories.find((cat) => cat.slug === slug)
}

function getAgeLabel(value) {
  return ageGroups.find((age) => age.value === value)?.label || value
}

function getAgeChipColor(ageGroup) {
  const colors = {
    '0-6': 'accent',
    '6-12': 'info',
    '1-2': 'secondary',
    '2-3': 'primary',
    '3+': 'warning',
  }
  return colors[ageGroup] || 'grey'
}

function showProductDetail(product) {
  selectedProduct.value = product
  showDialog.value = true
}

function clearFilters() {
  selectedCategory.value = 'all'
  selectedAgeGroup.value = 'all'
  searchQuery.value = ''
}
</script>

<style lang="scss" scoped>
.products-page {
  background: #f5f5f5;
}

.page-header {
  background: linear-gradient(135deg, $primary 0%, color-mix(in srgb, $primary 80%, black) 100%);
  position: relative;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }

  .container {
    position: relative;
    z-index: 1;
  }
}

.categories-section {
  background: white;
}

.category-card {
  transition: all 0.3s ease;
  border-radius: 12px;
  height: 100%;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  }

  &.active {
    border: 2px solid $primary;
    box-shadow: 0 4px 12px rgba($primary, 0.3);
  }
}

.product-card {
  transition: all 0.3s ease;
  border-radius: 16px;
  overflow: hidden;

  &:hover {
    transform: translateY(-8px);
    box-shadow: 0 12px 32px rgba(0, 0, 0, 0.15);
  }
}

.product-image-wrapper {
  overflow: hidden;
  border-radius: 16px 16px 0 0;
}

.product-image {
  transition: transform 0.3s ease;

  .product-card:hover & {
    transform: scale(1.1);
  }
}

.product-badges {
  position: absolute;
  top: 12px;
  right: 12px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.ellipsis-2-lines {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.product-detail-image {
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
}

.container {
  max-width: 1400px;
  margin: 0 auto;
}
</style>
