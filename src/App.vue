<template>
  <div>
    <Navbar />
    <Hero />
    <ProductSection />
    <AboutSection />
  </div>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import { defineAsyncComponent } from "vue";

const ProductSection = defineAsyncComponent(
  () => import("./components/ProductSection.vue"),
);
const AboutSection = defineAsyncComponent(
  () => import("./components/AboutSection.vue"),
);
</script>
