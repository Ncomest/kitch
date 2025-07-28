<script setup>
import ImageWrapper from "@components/shared/image-wrapper/ImageWrapper.vue";

defineProps({
  item: { type: Object, required: true },
});
</script>
<template>
  <div class="the-review">
    <ImageWrapper :src="item.ktch" :alt="item.name" class="the-review__image"/>
    <h3 class="the-review__name">{{ item.name }}</h3>
    <p class="the-review__text">
      {{ item.review }}
    </p>
  </div>
</template>
<style src="./style.scss"></style>
