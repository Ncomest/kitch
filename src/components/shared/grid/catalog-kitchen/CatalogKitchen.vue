<script setup>
import ImageWrapper from "@components/shared/image-wrapper/ImageWrapper.vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation } from "swiper/modules";
import kitchensData from "@/json/kitchens.json";
import calcDiscount from "@/helpers/calc-discount";

import "swiper/css";
import "swiper/css/navigation";

const kitchens = kitchensData;

// console.log(kitchensData)

// const kitchens = [
//   [
//     {
//       src: "/classic/kitchen-one.webp",
//       id: 1,
//       discount: 10,
//       price: 345000,
//       news: "акция действует до 31 августа",
//       sale: false,
//     },
//     {
//       src: "/classic/kitchen_2.webp",
//       id: 2,
//       discount: 5,
//       price: 315000,
//       news: "Рассрочка 0-0-12",
//       sale: false,
//     },
//     {
//       src: "/classic/kitchen_3.webp",
//       id: 3,
//       discount: 50,
//       price: 475000,
//       news: "Срок изготовления 30 дней",
//       sale: false,
//     },
//     {
//       src: "/classic/kitchen_4.webp",
//       id: 4,
//       discount: null,
//       price: 280000,
//       news: "Распродажа с выставки -50%",
//       sale: true,
//     },
//   ],
//   [
//     {
//       src: "/classic/kitchen-one.webp",
//       id: 1,
//       discount: 10,
//       price: 345000,
//       news: "акция действует до 31 августа",
//       sale: false,
//     },
//     {
//       src: "/classic/kitchen_2.webp",
//       id: 2,
//       discount: 5,
//       price: 315000,
//       news: "Рассрочка 0-0-12",
//       sale: false,
//     },
//     {
//       src: "/classic/kitchen_3.webp",
//       id: 3,
//       discount: 50,
//       price: 475000,
//       news: "Срок изготовления 30 дней",
//       sale: false,
//     },
//     {
//       src: "/classic/kitchen_4.webp",
//       id: 4,
//       discount: null,
//       price: 280000,
//       news: "Распродажа с выставки -50%",
//       sale: true,
//     },
//   ],
// ];
</script>

<template>
  <section class="catalog-kitchen">
    <h2 class="catalog-kitchen__hidden-anchor" id="catalog-kitchen"></h2>
    <Swiper
      :modules="[Autoplay, Navigation]"
      :speed="1500"
      :autoplay="{ delay: 8000, pauseOnMouseEnter: true }"
      :space-between="10"
      :loop="true"
      :navigation="{
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      }"
    >
      <SwiperSlide v-for="(kitchen, index) in kitchens" :key="index">
        <div class="catalog-kitchen__grid">
          <div
            class="catalog-kitchen__grid-item"
            v-for="item in kitchen"
            :key="item.id"
          >
            <span
              class="catalog-kitchen__grid-item__label"
              v-show="item.discount"
            >
              -{{ item.discount }}%
            </span>

            <span class="catalog-kitchen__grid-item__label" v-show="item.sale">
              Распродажа
            </span>
            <ImageWrapper
              :src="item.src"
              alt="name"
              :key="item.id"
              class="catalog-kitchen__grid-image"
            />
            <span class="catalog-kitchen__grid-item__news">{{
              item.news
            }}</span>
            <div class="catalog-kitchen__grid-item__price-container">
              <p
                class="catalog-kitchen__grid-item__price-old"
                v-show="item.discount"
              >
                {{ calcDiscount(item.price, item.discount) }}₽
              </p>
              <p class="catalog-kitchen__grid-item__price">
                {{ item.price.toLocaleString("ru-RU") }}₽
              </p>
            </div>
          </div>
        </div>
      </SwiperSlide>
      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>
    </Swiper>
  </section>
</template>
<style src="./style.scss"></style>
