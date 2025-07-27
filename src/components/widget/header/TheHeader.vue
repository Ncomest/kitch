<script setup>
import TheLogo from "@components/shared/logo/TheLogo.vue";
import TheLink from "@components/shared/link/the-link/TheLink.vue";
import TheBurger from "@components/shared/buttons/burger/TheBurger.vue";
import { useSidePanel } from "@stores/side-panel";

const burger = useSidePanel();
</script>
<template>
  <div class="the-header">
    <TheLogo />
    <nav class="the-header__navbar">
      <TheLink text="Заказать" />
      <TheLink text="Каталог" />
      <TheLink text="О нас" />
    </nav>
    <TheBurger class="the-header__burger" @click="burger.toggle()"/>
  </div>
</template>
<style src="./style.scss"></style>
