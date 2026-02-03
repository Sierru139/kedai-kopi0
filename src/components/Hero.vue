<template>
  <section
    id="home"
    class="relative h-screen md:grid grid-cols-2 flex overflow-hidden"
  >
    <!-- Optimized LCP Background Image -->
    <img
      src="/img/coffeebg.jpg"
      alt=""
      class="absolute inset-0 w-full h-full object-cover -z-10"
      fetchpriority="high"
      aria-hidden="true"
    />

    <div
      class="flex flex-col col-span-1 items-start justify-center md:pl-10 pl-3 z-10"
    >
      <h1 class="text-6xl font-bold jdlhome text-white">
        Nikmati suasana di
        <span
          class="bg-clip-text text-transparent bg-gradient-to-l from-[#c9a570] via-[#9a6c4a] to-[#c9a570]"
          >Kedai Sudut</span
        >
      </h1>
      <p
        class="mt-3 mb-2 text-xl md:text-2xl text-[#e8bd7d] font-light leading-relaxed max-w-lg shadow-black drop-shadow-md"
      >
        Menyuguhkan kehangatan, merayakan pertemuan. Jadikan setiap kunjungan di
        kedai sudut kami sebagai bagian manis dari ceritamu hari ini.
      </p>
    </div>
    <div class=""></div>
  </section>
</template>

<script setup></script>
