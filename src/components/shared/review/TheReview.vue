<script setup>
defineProps({
  text: { type: String, required: true },
  reviewName: { type: String, required: true },
});
</script>
<template>
  <div class="the-review">
    <h3 class="the-review__name">{{ reviewName }}</h3>
    <p class="the-review__text">
      {{ text }}
    </p>
  </div>
</template>
<style src="./style.scss"></style>
