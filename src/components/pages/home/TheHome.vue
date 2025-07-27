<script setup>
import MainSlider from "@components/widget/slider/main-slider/MainSlider.vue";
import OurDesigner from "@components/section/ourDesigner/OurDesigner.vue";
import OurReviews from "@components/section/ourReviews/OurReviews.vue";
</script>
<template>
  <main class="the-home">
    <MainSlider class="the-home__main-slider" />
    <OurDesigner />
    <OurReviews />
  </main>
</template>
<style src="./style.scss"></style>
