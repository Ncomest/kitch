<script setup>
import ImageWrapper from "@components/shared/image-wrapper/ImageWrapper.vue";

const kitchens = [
  { src: "/classic/kitchen-one.webp", id: 1, discount: 10, price: 345000 },
  { src: "/classic/kitchen_2.webp", id: 2, discount: 5, price: 315000 },
  { src: "/classic/kitchen_3.webp", id: 3, discount: 50, price: 475000 },
  { src: "/classic/kitchen_4.webp", id: 4, discount: null, price: 280000 },
];
</script>

<template>
  <section class="catalog-kitchen" id="catalog-kitchen">
    <div class="catalog-kitchen__container">
      <h2 class="catalog-kitchen__title">Каталог кухонь</h2>
      <div class="catalog-kitchen__grid">
        <div class="catalog-kitchen__grid-item" v-for="item in kitchens">
          <span
            class="catalog-kitchen__grid-item__label"
            v-show="item.discount"
          >
            -{{ item.discount }}%
          </span>
          <ImageWrapper
            :src="item.src"
            alt="name"
            :key="item.id"
            class="catalog-kitchen__grid-image"
          />
          <div class="catalog-kitchen__grid-item__price-container">
            <p class="catalog-kitchen__grid-item__price-old" v-show="item.discount">{{ item.price.toLocaleString('de-DE') }}р</p>
            <p class="catalog-kitchen__grid-item__price">{{ item.price.toLocaleString('de-DE') }}р</p>
          </div>
          <button class="catalog-kitchen__grid-button">Хочу такую!</button>
        </div>
      </div>
    </div>
  </section>
</template>
<style src="./style.scss"></style>
