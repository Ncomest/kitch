<script setup>
import ImageWrapper from "@components/shared/image-wrapper/ImageWrapper.vue";

const images = [
  { ktch: "/classic/kitchen-one.webp", id: 1 },
  { ktch: "/classic/kitchen_2.webp", id: 2 },
  { ktch: "/classic/kitchen_3.webp", id: 3 },
  { ktch: "/classic/kitchen_4.webp", id: 4 },
];
</script>

<template>
  <section class="catalog-kitchen">
    <div class="catalog-kitchen__container">
      <h2 class="catalog-kitchen__title">Каталог кухонь</h2>

      <div class="catalog-kitchen__grid">
        <div class="catalog-kitchen__grid-item" v-for="image in images">
          <ImageWrapper :src="image.ktch" alt="name" :key="image.id" class="catalog-kitchen__grid-image"/>
          <button class="catalog-kitchen__grid-button">Хочу такую!</button>
        </div>
      </div>
    </div>
  </section>
</template>
<style src="./style.scss"></style>
