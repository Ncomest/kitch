<script setup>
import "swiper/css";
import "swiper/css/pagination";

import { onMounted, ref } from "vue";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Pagination } from "swiper/modules";
import ImageWrapper from "@components/shared/image-wrapper/ImageWrapper.vue";
import kitchenImage from "/classic/kitchen-one.webp";

const slides = ref([]);
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
      :autoplay="{ delay: 5000 }"
    >
      <SwiperSlide v-for="i in 4" :key="i">
        <ImageWrapper
          src="/classic/kitchen-one.webp"
          alt="Kitchen"
          class="swiper__image-wrapper"
        />
      </SwiperSlide>
    </Swiper>
  </div>
</template>
<style src="./style.scss"></style>
