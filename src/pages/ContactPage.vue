<template>
  <q-page>
    <!-- Hero Section -->
    <section class="contact-hero text-center text-white q-pa-xl">
      <h1 class="text-h2 text-weight-bold q-mb-md">İletişim</h1>
      <p class="text-h6">XAY Oyuncak | Sorularınız için buradayız</p>
    </section>

    <!-- Contact Content -->
    <section class="q-pa-xl">
      <div class="row q-col-gutter-xl">
        <!-- Contact Form -->
        <div class="col-12 col-md-7">
          <q-card flat bordered class="contact-form-card q-pa-xl">
            <h3 class="text-h4 text-weight-bold text-primary q-mb-md">Bize Ulaşın</h3>
            <p class="text-body1 text-grey-7 q-mb-lg">
              Sorularınız, önerileriniz veya işbirliği talepleriniz için formu doldurun, size en kısa sürede dönüş
              yapalım.
            </p>

            <q-form @submit="onSubmit" class="q-gutter-md">
              <div class="row q-col-gutter-md">
                <div class="col-12 col-sm-6">
                  <q-input
                    v-model="form.firstName"
                    label="Ad *"
                    outlined
                    lazy-rules
                    :rules="[(val) => (val && val.length > 0) || 'Lütfen adınızı girin']"
                  />
                </div>
                <div class="col-12 col-sm-6">
                  <q-input
                    v-model="form.lastName"
                    label="Soyad *"
                    outlined
                    lazy-rules
                    :rules="[(val) => (val && val.length > 0) || 'Lütfen soyadınızı girin']"
                  />
                </div>
              </div>

              <q-input
                v-model="form.email"
                label="E-posta *"
                type="email"
                outlined
                lazy-rules
                :rules="[
                  (val) => (val && val.length > 0) || 'Lütfen e-posta adresinizi girin',
                  (val) => /.+@.+\..+/.test(val) || 'Geçerli bir e-posta adresi girin',
                ]"
              />

              <q-input v-model="form.phone" label="Telefon" type="tel" outlined />

              <q-input v-model="form.company" label="Firma/Kurum" outlined />

              <q-select
                v-model="form.subject"
                :options="subjectOptions"
                label="Konu *"
                outlined
                emit-value
                map-options
                lazy-rules
                :rules="[(val) => val !== null || 'Lütfen bir konu seçin']"
              />

              <q-input
                v-model="form.message"
                label="Mesajınız *"
                type="textarea"
                outlined
                rows="6"
                lazy-rules
                :rules="[(val) => (val && val.length > 0) || 'Lütfen mesajınızı yazın']"
              />

              <q-toggle v-model="form.consent" class="q-mb-md">
                <span class="text-caption">
                  <a href="#" class="text-primary">KVKK Aydınlatma Metni</a>'ni okudum ve kabul ediyorum. *
                </span>
              </q-toggle>

              <div class="row q-col-gutter-md">
                <div class="col-12 col-sm-6">
                  <q-btn
                    :loading="loading"
                    type="submit"
                    unelevated
                    rounded
                    color="primary"
                    label="Gönder"
                    class="full-width"
                    size="lg"
                    no-caps
                    :disable="!form.consent"
                  />
                </div>
                <div class="col-12 col-sm-6">
                  <q-btn
                    @click="resetForm"
                    outline
                    rounded
                    color="primary"
                    label="Temizle"
                    class="full-width"
                    size="lg"
                    no-caps
                  />
                </div>
              </div>
            </q-form>
          </q-card>
        </div>

        <!-- Contact Info -->
        <div class="col-12 col-md-5">
          <div class="q-gutter-lg">
            <!-- Contact Cards -->
            <q-card flat bordered class="contact-info-card q-pa-lg">
              <div class="row items-center q-mb-md">
                <q-icon name="location_on" size="40px" color="primary" class="q-mr-md" />
                <div>
                  <div class="text-h6 text-weight-bold">Adres</div>
                  <div class="text-body2 text-grey-7">Merkez Ofis</div>
                </div>
              </div>
              <p class="text-body2 q-ma-none">
                XAY Oyuncak A.Ş.<br />
                Fahrettin Altay Mahallesi 65 Sokak No:11/E<br />
                Karabağlar / İzmir, Türkiye
              </p>
            </q-card>

            <q-card flat bordered class="contact-info-card q-pa-lg">
              <div class="row items-center q-mb-md">
                <q-icon name="phone" size="40px" color="accent" class="q-mr-md" />
                <div>
                  <div class="text-h6 text-weight-bold">Telefon</div>
                  <div class="text-body2 text-grey-7">Size ulaşalım</div>
                </div>
              </div>
              <p class="text-body2 q-ma-none">
                <strong>Satış:</strong> +90 (216) 555 12 34<br />
                <strong>Müşteri Hizmetleri:</strong> +90 (216) 555 12 35<br />
                <strong>Fax:</strong> +90 (216) 555 12 36
              </p>
            </q-card>

            <q-card flat bordered class="contact-info-card q-pa-lg">
              <div class="row items-center q-mb-md">
                <q-icon name="email" size="40px" color="secondary" class="q-mr-md" />
                <div>
                  <div class="text-h6 text-weight-bold">E-posta</div>
                  <div class="text-body2 text-grey-7">Hızlı yanıt</div>
                </div>
              </div>
              <p class="text-body2 q-ma-none">
                <strong>Genel:</strong> info@xay.com.tr<br />
                <strong>Satış:</strong> satis@xay.com.tr<br />
                <strong>Destek:</strong> destek@xay.com.tr
              </p>
            </q-card>

            <q-card flat bordered class="contact-info-card q-pa-lg">
              <div class="row items-center q-mb-md">
                <q-icon name="schedule" size="40px" color="warning" class="q-mr-md" />
                <div>
                  <div class="text-h6 text-weight-bold">Çalışma Saatleri</div>
                  <div class="text-body2 text-grey-7">Ofis saatleri</div>
                </div>
              </div>
              <p class="text-body2 q-ma-none">
                <strong>Hafta İçi:</strong> 09:00 - 18:00<br />
                <strong>Cumartesi:</strong> 09:00 - 14:00<br />
                <strong>Pazar:</strong> Kapalı
              </p>
            </q-card>

            <!-- Social Media -->
            <q-card flat bordered class="contact-info-card q-pa-lg text-center">
              <div class="text-h6 text-weight-bold q-mb-md">Sosyal Medya</div>
              <div class="row justify-center q-gutter-md">
                <q-btn round size="lg" color="primary" icon="facebook" @click="openSocialMedia('facebook')" />
                <q-btn round size="lg" color="info" icon="twitter" @click="openSocialMedia('twitter')" />
                <q-btn round size="lg" color="secondary" icon="facebook" @click="openSocialMedia('instagram')" />
                <q-btn round size="lg" color="negative" icon="play_arrow" @click="openSocialMedia('youtube')" />
              </div>
            </q-card>
          </div>
        </div>
      </div>
    </section>

    <!-- Map Section -->
    <section class="q-pa-xl bg-grey-2">
      <div class="text-center q-mb-lg">
        <h3 class="text-h4 text-weight-bold text-primary q-mb-md">Bizi Ziyaret Edin</h3>
        <p class="text-body1 text-grey-7">Showroom'umuza gelerek ürünlerimizi yerinde inceleyebilirsiniz</p>
      </div>

      <q-card flat bordered class="map-card">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3127.9876544!2d27.1234567!3d38.4123456!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMzjCsDI0JzQ0LjQiTiAyN8KwMDcnMjQuNCJF!5e0!3m2!1str!2str!4v1234567890123!5m2!1str!2str"
          width="100%"
          height="450"
          style="border:0;"
          allowfullscreen=""
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          title="XAY Oyuncak Konum"
        ></iframe>
      </q-card>
    </section>

    <!-- FAQ Section -->
    <section class="q-pa-xl bg-white">
      <div class="text-center q-mb-xl">
        <h3 class="text-h4 text-weight-bold text-primary q-mb-md">Sıkça Sorulan Sorular</h3>
        <p class="text-body1 text-grey-7">Aklınıza takılan sorular</p>
      </div>

      <div class="row justify-center">
        <div class="col-12 col-md-10">
          <q-list bordered separator class="rounded-borders">
            <q-expansion-item
              v-for="(faq, index) in faqs"
              :key="index"
              :icon="faq.icon"
              :label="faq.question"
              header-class="text-primary text-weight-bold"
              expand-icon-class="text-primary"
            >
              <q-card flat>
                <q-card-section class="text-grey-8">
                  {{ faq.answer }}
                </q-card-section>
              </q-card>
            </q-expansion-item>
          </q-list>
        </div>
      </div>
    </section>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()
const loading = ref(false)

const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  company: '',
  subject: null,
  message: '',
  consent: false,
})

const subjectOptions = [
  { label: 'Ürün Bilgisi', value: 'product' },
  { label: 'Satış / Distribütörlük', value: 'sales' },
  { label: 'Teknik Destek', value: 'support' },
  { label: 'İşbirliği Teklifi', value: 'partnership' },
  { label: 'Diğer', value: 'other' },
]

const faqs = ref([
  {
    icon: 'inventory_2',
    question: 'Ürünleriniz hangi yaş gruplarına uygun?',
    answer:
      'Ürünlerimiz 0-2 yaş, 3-5 yaş, 6-8 yaş ve 9+ yaş grupları için özel olarak tasarlanmıştır. Her ürünün detay sayfasında uygun yaş grubu belirtilmiştir.',
  },
  {
    icon: 'verified_user',
    question: 'Ürünleriniz güvenli mi?',
    answer:
      'Tüm ürünlerimiz CE, EN 71, ASTM gibi uluslararası güvenlik standartlarına uygun olarak üretilmiştir. Düzenli testlerden geçirilir ve sertifikalıdır.',
  },
  {
    icon: 'local_shipping',
    question: 'Kargo süreci nasıl işliyor?',
    answer:
      'Siparişleriniz 1-2 iş günü içerisinde kargoya verilir. Kargo süresi bölgenize göre 2-5 iş günü arasında değişmektedir. Ücretsiz kargo kampanyalarımızı düzenli olarak takip edebilirsiniz.',
  },
  {
    icon: 'store',
    question: 'Nereden satın alabilirim?',
    answer:
      'Ürünlerimizi tüm Türkiye\'deki büyük oyuncak mağazalarında, marketlerde ve online satış platformlarında bulabilirsiniz. Distribütör listesi için bizimle iletişime geçebilirsiniz.',
  },
  {
    icon: 'autorenew',
    question: 'İade ve değişim politikanız nedir?',
    answer:
      'Ürünlerinizi satın aldığınız tarihten itibaren 14 gün içerisinde, kullanılmamış ve orijinal ambalajında olmak kaydıyla iade edebilirsiniz. Hasarlı veya hatalı ürünler için garanti kapsamında ücretsiz değişim yapılır.',
  },
  {
    icon: 'business',
    question: 'Toptan satış yapıyor musunuz?',
    answer:
      'Evet, distribütörler ve büyük alıcılar için özel fiyatlandırma yapıyoruz. Toptan satış için lütfen satis@xay.com.tr adresinden bizimle iletişime geçin.',
  },
])

async function onSubmit() {
  if (!form.value.consent) {
    $q.notify({
      type: 'warning',
      message: 'Lütfen KVKK metnini okuyun ve onaylayın',
      position: 'top',
    })
    return
  }

  loading.value = true

  // Simulate API call
  setTimeout(() => {
    loading.value = false

    $q.notify({
      type: 'positive',
      message: 'Mesajınız başarıyla gönderildi! En kısa sürede size dönüş yapacağız.',
      position: 'top',
      timeout: 3000,
    })

    resetForm()
  }, 1500)
}

function resetForm() {
  form.value = {
    firstName: '',
    lastName: '',
    email: '',
    phone: '',
    company: '',
    subject: null,
    message: '',
    consent: false,
  }
}

function openSocialMedia(platform) {
  $q.notify({
    type: 'info',
    message: `${platform.charAt(0).toUpperCase() + platform.slice(1)} sayfamıza yönlendiriliyorsunuz...`,
    position: 'top',
  })

  // Sosyal medya linklerini buraya ekleyebilirsiniz
  // const url = `https://${platform}.com/xayoyuncak`
  // window.open(url, '_blank')
}
</script>

<style lang="scss" scoped>
.contact-hero {
  background: linear-gradient(135deg, $accent 0%, color-mix(in srgb, $accent 90%, black) 100%);
  min-height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.contact-form-card,
.contact-info-card {
  border-radius: 16px;
}

.contact-info-card {
  transition: all 0.3s ease;

  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  }
}

.map-card {
  border-radius: 16px;
  overflow: hidden;
}

.map-placeholder {
  min-height: 400px;
  background: linear-gradient(135deg, #f5f5f5 0%, #e0e0e0 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
