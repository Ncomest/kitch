<script setup>
import "swiper/css";
import "swiper/css/pagination";

import { onMounted, ref } from "vue";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Pagination } from "swiper/modules";
import ImageWrapper from "@components/shared/image-wrapper/ImageWrapper.vue";

const slides = [
  { ktch: "/classic/kitchen-one.webp", id: 1 },
  { ktch: "/classic/kitchen_2.webp", id: 2 },
  { ktch: "/classic/kitchen_3.webp", id: 3 },
  { ktch: "/classic/kitchen_4.webp", id: 4 },
];

// const slides = ref([]);
const swiperRef = ref(null);
</script>

<template>
  <div>
    <Swiper
      :modules="[Pagination, Autoplay]"
      :pagination="{ clickable: true }"
      :slides-per-view="1"
      :space-between="10"
      :loop="true"
      :speed="1500"
      :autoplay="{ delay: 15000 }"
    >
      <SwiperSlide v-for="i in slides" :key="i.id">
        <ImageWrapper
          :src="i.ktch"
          alt="Kitchen"
          class="swiper__image-wrapper"
        />
      </SwiperSlide>
    </Swiper>
  </div>
</template>
<style src="./style.scss"></style>
