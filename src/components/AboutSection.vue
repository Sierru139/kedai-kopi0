<template>
  <section class="grid md:grid-cols-3 md:grid-rows-2 grid-rows-4 bg-gradient-to-b from-[#7d5235] to-[#8b491a] text-white">
    <div class="md:col-span-3 about1">
      <div class="w-full h-full backdrop-blur-sm backdrop-sepia backdrop-brightness-50 flex flex-col justify-center items-center textabout">
        <h1 class="text-5xl font-bold">Tentang Kami</h1>
        <p class="font-light">Semua memiliki sejarahnya, termasuk Koppi</p>
      </div>
    </div>
    
    <div class="bg-[#c47c4c]">
      <div class="p-4 flex flex-col items-center justify-center text-justify">
        <h1 class="text-2xl">Koppi? Bentar, apa itu ?</h1>
        <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ratione fugit nulla illo iusto, error est doloribus voluptatem eveniet aspernatur. Maiores assumenda nihil, aperiam, autem laborum expedita excepturi cum tenetur, aliquid ex possimus facilis quos? Maiores quasi adipisci tempora laudantium cupiditate!</p>
      </div>
    </div>
    
    <div class="bg-[#b4754a]">
      <div class="p-4 flex flex-col items-center justify-center text-justify">
        <h1 class="text-2xl">Sejarahnya gimana ?</h1>
        <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ratione fugit nulla illo iusto, error est doloribus voluptatem eveniet aspernatur. Maiores assumenda nihil, aperiam, autem laborum expedita excepturi cum tenetur, aliquid ex possimus facilis quos? Maiores quasi adipisci tempora laudantium cupiditate!</p>
      </div>
    </div>
    
    <div class="bg-[#c47c4c]">
      <div class="p-4 flex flex-col items-center justify-center text-justify">
        <h1 class="text-2xl">Keren nih, share lock dong</h1>
        <div class="flex gap-x-2">
          <iframe 
            class="w-[50%]" 
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d113626.5738518997!2d-109.46784074945269!3d-27.130150361803185!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x99481bd912a875cb%3A0x2d7629d40aea00db!2sMoai!5e0!3m2!1sen!2sid!4v1710226719923!5m2!1sen!2sid"  
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
          <div class="w-[50%]">
            <ul>&#x2022;  Lokasi :
              <li>Laut Jl. Moai</li>
            </ul>
            <br>
            <ul>&#x2022;  No Telepon :
              <li>0852554422</li>
            </ul>
            <br>
            <ul>&#x2022;  Email :
              <li>yasirbanggw@gmail.com</li>
            </ul>
          </div>
        </div>
        <div class="mt-3 w-full">
          <h1 class="text-sm">berlangganan dengan kami</h1>
          <input class="w-full" placeholder="example@gmail.com" type="text">
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>
