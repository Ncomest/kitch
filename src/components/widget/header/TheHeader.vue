<script setup>
import TheLogo from "@components/shared/logo/TheLogo.vue";
import TheLink from "@components/shared/link/the-link/TheLink.vue";
import TheBurger from "@components/shared/buttons/burger/TheBurger.vue";

</script>
<template>
  <div class="the-header">
    <TheLogo />
    <nav class="the-header__navbar">
      <TheLink text="Заказать" href="#post-order" />
      <TheLink text="Каталог" href="#catalog-kitchen" />
      <TheLink text="О нас" href="#about-us" />
    </nav>
    <TheBurger />
  </div>
</template>
<style src="./style.scss"></style>
