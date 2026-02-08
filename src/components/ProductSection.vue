<template>
  <section
    id="product"
    class="bg-gradient-to-t from-[#7d5235] to-[#8b491a] flex md:flex-row flex-col"
  >
    <div
      class="md:w-[30%] w-full h-full bg-[#cb9544] border-r border-white max-md:border-b"
    >
      <!-- Category Switch (Persistent) -->
      <div class="top-4 left-4 z-20 flex">
        <button
          @click="setCategory('makanan')"
          :class="[
            'transition-all duration-300 shadow-md flex-grow',
            activeCategory === 'makanan'
              ? 'bg-white text-[#8b491a] font-bold'
              : 'bg-[#8b491a] text-white hover:bg-[#a05a2c]',
          ]"
        >
          Makanan
        </button>
        <button
          @click="setCategory('minuman')"
          :class="[
            'transition-all duration-300 shadow-md flex-grow',
            activeCategory === 'minuman'
              ? 'bg-white text-[#8b491a] font-bold'
              : 'bg-[#8b491a] text-white hover:bg-[#a05a2c]',
          ]"
        >
          Minuman
        </button>
      </div>

      <div class="h-fit md:grid hidden cursor-pointer">
        <div
          v-for="menu in filteredMenus"
          :key="menu.id"
          :class="[
            'text-yellow-500 flex items-center text-2xl border-b border-gray-400 h-20',
            menu.imgClass,
          ]"
        >
          <p
            class="w-full px-8 flex items-center h-full backdrop-blur-[2px] menu-coffee bg-[rgba(0,0,0,0.4)]"
            @click="selectMenu(menu.id)"
          >
            {{ menu.name }}
          </p>
        </div>
      </div>

      <div class="h-fit w-full md:hidden flex flex-col cursor-pointer">
        <div
          v-for="menu in filteredMenus"
          :key="'mobile-' + menu.id"
          :class="[
            'text-yellow-500 flex items-center text-2xl border-b border-gray-400 h-20',
            menu.imgClass,
          ]"
        >
          <p
            class="w-full px-8 flex items-center h-full backdrop-blur-[2px] menu-coffee bg-[rgba(0,0,0,0.4)]"
            @click="selectMenu(menu.id)"
          >
            {{ menu.name }}
          </p>
        </div>
      </div>
    </div>

    <!-- IMAGE REVIEW -->

    <div
      class="md:w-[30%] max-md:min-h-[220px] w-full bg-[#cb9544] z-10 overflow-hidden relative flex flex-col justify-end items-end border-r border-white max-md:border-b"
    >
      <div v-if="selectedMenu === null" class="backdrop-blur-sm p-5 mt-16">
        <h1 class="text-3xl font-semibold">Pilih Menu</h1>
        <p>
          Pilih menu yang sesuai dengan selera anda, nikmati dengan sepenuh hati
          😊~
        </p>
      </div>

      <template v-for="menu in filteredMenus" :key="menu.id">
        <div
          v-if="selectedMenu === menu.id"
          :class="[
            'menuDesc menuAnim text-white p-5 h-full w-full flex-grow',
            menu.descClass,
          ]"
        >
          <!-- <h1 class="text-3xl font-semibold">{{ menu.name }}</h1>
            <p>{{ menu.shortDesc }}</p> -->
        </div>
      </template>
    </div>
    <!-- IMAGE REVIEW END -->

    <!-- IMAGE DESCRIPTION -->
    <div class="md:h-full md:w-[40%] w-full flex">
      <div v-if="selectedMenu === null" class="w-full p-5">
        <div class="border-b">
          <h3 class="font-semibold text-4xl">
            Pilih menu untuk melihat detailnya
          </h3>
          <p class="text-2xl">Rp ???????</p>
          <p class="my-1">Rating :</p>
          <p class="text-yellow-300 text-2xl p-1 mt-2"></p>
        </div>
        <div>
          <!-- <div>
            <h4 class="text-xl">Rasa :</h4>
            <div class="grid grid-rows-2 grid-cols-2 border-b">
              <p>Pahit <span class="text-xl text-yellow-300">0%</span></p>
              <p>Manis <span class="text-xl text-yellow-300">0%</span></p>
              <p>Asin <span class="text-xl text-yellow-300">0%</span></p>
              <p>Asam <span class="text-xl text-yellow-300">0%</span></p>
            </div>
          </div> -->
          <div>
            <h3 class="text-xl mt-2">Tentang menu ini:</h3>
            <p class="text-justify mt-2">
              Pilih menu untuk mengetahui detailnya
            </p>
          </div>
        </div>
      </div>

      <template v-for="menu in filteredMenus" :key="menu.id">
        <div v-if="selectedMenu === menu.id" class="w-full p-5 menuAnim">
          <div class="border-b">
            <h3 class="font-semibold text-4xl">{{ menu.name }}</h3>
            <p class="text-2xl">{{ menu.price }}</p>
            <p class="my-1">Rating :</p>
            <p class="text-yellow-300 text-2xl p-1 mt-2">
              <i
                v-for="n in menu.rating.full"
                :key="'full-' + n"
                class="fas fa-star"
              ></i>
              <i v-if="menu.rating.half" class="fas fa-star-half-alt"></i>
            </p>
            <button
              class="px-6 py-2 bg-[#8b652c] active:bg-[#6e4b20] rounded-md md:mt-3 mb-2 mt-3 font-semibold text-white duration-150 hover:-translate-y-[1px]"
            >
              Beli Sekarang
            </button>
          </div>
          <div>
            <!-- <div>
              <h4 class="text-xl">Rasa :</h4>
              <div class="grid grid-cols-2 border-b">
                <p>
                  Pahit
                  <span class="text-xl text-yellow-300"
                    >{{ menu.taste.bitter }}%</span
                  >
                </p>
                <p>
                  Manis
                  <span class="text-xl text-yellow-300"
                    >{{ menu.taste.sweet }}%</span
                  >
                </p>
                <p>
                  Asin
                  <span class="text-xl text-yellow-300"
                    >{{ menu.taste.salty }}%</span
                  >
                </p>
                <p>
                  Asam
                  <span class="text-xl text-yellow-300"
                    >{{ menu.taste.sour }}%</span
                  >
                </p>
              </div>
            </div> -->
            <div>
              <h3 class="text-xl mt-2">Tentang Menu ini:</h3>
              <p class="text-justify mt-2">{{ menu.description }}</p>
            </div>
          </div>
        </div>
      </template>
    </div>
    <!-- IMAGE DESCRIPTION END -->
  </section>
</template>

<script setup>
import { ref, computed } from "vue";

const selectedMenu = ref(null);
const activeCategory = ref("makanan");

const menus = [
  // Makanan
  {
    id: 1,
    name: "Nasi Goreng",
    category: "makanan",
    shortDesc: "Lezat, Gurih, dan Mengenyangkan.",
    price: "Rp 20.000,00-",
    rating: { full: 4, half: true },
    // taste: { bitter: 0, sweet: 10, salty: 60, sour: 5 },
    description:
      "Nasi goreng spesial dengan bumbu rahasia yang menggugah selera, disajikan dengan telur mata sapi dan kerupuk.",
    imgClass: "nasreng", // Placeholder reusing existing class
    descClass: "descnasreng",
  },
  {
    id: 2,
    name: "Kentang Goreng",
    category: "makanan",
    shortDesc: "Renyah, Gurih, dan Ringan.",
    price: "Rp 15.000,00-",
    rating: { full: 4, half: false },
    // taste: { bitter: 0, sweet: 5, salty: 80, sour: 0 },
    description:
      "Kentang goreng pilihan yang digoreng hingga keemasan, cocok untuk teman ngemil santai.",
    imgClass: "kentang",
    descClass: "desckentang",
  },
  {
    id: 3,
    name: "Indomie",
    category: "makanan",
    shortDesc: "Klasik, Nikmat, dan Praktis.",
    price: "Rp 12.000,00-",
    rating: { full: 5, half: false },
    // taste: { bitter: 0, sweet: 10, salty: 70, sour: 5 },
    description:
      "Indomie goreng atau rebus dengan topping telur dan sayuran, selera anak kost yang mendunia.",
    imgClass: "indomie",
    descClass: "descindomie",
  },
  {
    id: 4,
    name: "Bakso",
    category: "makanan",
    shortDesc: "Hangat, Kenyal, dan Berkuah.",
    price: "Rp 18.000,00-",
    rating: { full: 5, half: false },
    // taste: { bitter: 0, sweet: 5, salty: 65, sour: 10 },
    description:
      "Bakso sapi asli dengan kuah kaldu yang gurih dan segar, lengkap dengan mie dan sayuran.",
    imgClass: "bakso",
    descClass: "descbakso",
  },
  // Minuman
  {
    id: 5,
    name: "Cappucino",
    category: "minuman",
    shortDesc: "Kreami, Berbusa, dan Hangat.",
    price: "Rp 40.000,00-",
    rating: { full: 5, half: false },
    // taste: { bitter: 10, sweet: 76, salty: 5, sour: 5 },
    description:
      "Cappuccino adalah minuman kopi yang terdiri dari espresso, susu, dan busa susu.",
    imgClass: "cappuccino",
    descClass: "desccappuccino",
  },
  {
    id: 6,
    name: "Coklat",
    category: "minuman",
    shortDesc: "Manis, Lembut, dan Menenangkan.",
    price: "Rp 25.000,00-",
    rating: { full: 4, half: true },
    // taste: { bitter: 5, sweet: 80, salty: 0, sour: 0 },
    description:
      "Minuman coklat kental yang manis dan hangat, cocok untuk memanjakan diri.",
    imgClass: "chocolate",
    descClass: "descchocolate",
  },
  {
    id: 7,
    name: "Vanilla",
    category: "minuman",
    shortDesc: "Harum, Manis, dan Creamy.",
    price: "Rp 28.000,00-",
    rating: { full: 4, half: false },
    // taste: { bitter: 0, sweet: 85, salty: 0, sour: 0 },
    description:
      "Minuman rasa vanilla yang lembut dan creamy, memberikan sensasi ketenangan.",
    imgClass: "vanilla",
    descClass: "descvanilla",
  },
  {
    id: 8,
    name: "Taro",
    category: "minuman",
    shortDesc: "Unik, Manis, dan Ungu.",
    price: "Rp 28.000,00-",
    rating: { full: 4, half: true },
    // taste: { bitter: 0, sweet: 75, salty: 5, sour: 0 },
    description:
      "Minuman rasa taro dengan warna ungu yang khas dan rasa manis yang unik.",
    imgClass: "taro",
    descClass: "desctaro",
  },
  {
    id: 9,
    name: "Thaitea",
    category: "minuman",
    shortDesc: "Segar, Manis, dan Otentik.",
    price: "Rp 22.000,00-",
    rating: { full: 5, half: false },
    // taste: { bitter: 5, sweet: 80, salty: 0, sour: 0 },
    description:
      "Teh susu khas Thailand dengan aroma rempah yang kuat dan rasa manis yang pas.",
    imgClass: "thai-tea",
    descClass: "descthai-tea",
  },
  {
    id: 10,
    name: "Greentea",
    category: "minuman",
    shortDesc: "Sehat, Segar, dan Alami.",
    price: "Rp 25.000,00-",
    rating: { full: 4, half: true },
    // taste: { bitter: 10, sweet: 60, salty: 0, sour: 5 },
    description:
      "Minuman teh hijau yang kaya antioksidan, segar dan menyehatkan.",
    imgClass: "green-tea",
    descClass: "descgreen-tea",
  },
];

const filteredMenus = computed(() => {
  return menus.filter((menu) => menu.category === activeCategory.value);
});

const currentMenu = computed(() => {
  return menus.find((m) => m.id === selectedMenu.value);
});

const selectMenu = (menuId) => {
  selectedMenu.value = menuId;
  // Ensure we don't need to reset anything else, but good to keep in mind
};

const setCategory = (category) => {
  activeCategory.value = category;
  selectedMenu.value = null;
};
</script>

<style scoped>
.cappuccino,
.chocolate,
.vanilla,
.green-tea,
.thai-tea,
.taro,
.nasreng,
.kentang,
.bakso,
.indomie {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.desccappuccino,
.descchocolate,
.descvanilla,
.descgreen-tea,
.descthai-tea,
.desctaro,
.descnasreng,
.desckentang,
.descbakso,
.descindomie {
  animation: masuk 2s ease-in-out;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.cappuccino,
.desccappuccino {
  background-image: url(/img/minuman/cappuccino.jpg);
}
.chocolate,
.descchocolate {
  background-image: url(/img/minuman/chocolate.jpg);
}
.vanilla,
.descvanilla {
  background-image: url(/img/minuman/vanilla.jpg);
}
.thai-tea,
.descthai-tea {
  background-image: url(/img/minuman/thai-tea.jpg);
}
.taro,
.desctaro {
  background-image: url(/img/minuman/taro.jpg);
}
.green-tea,
.descgreen-tea {
  background-image: url(/img/minuman/green-tea.jpg);
}

.nasreng,
.descnasreng {
  background-image: url(/img/makanan/nasi-goreng.jpg);
}
.kentang,
.desckentang {
  background-image: url(/img/makanan/kentang-goreng.jpg);
}
.bakso,
.descbakso {
  background-image: url(/img/makanan/bakso.jpg);
}
.indomie,
.descindomie {
  background-image: url(/img/makanan/indomie.jpg);
}

.menuAnim {
  animation: detmasuk 0.2s linear;
}

.menu-coffee {
  transition-duration: 1s;
}

.menu-coffee:hover {
  box-shadow: inset 0px -200px 0px rgba(55, 33, 22, 0.982);
}

@keyframes masuk {
  0% {
    transform: translateY(300px);
  }
  100% {
    transform: translateY(0);
  }
}

@keyframes detmasuk {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
