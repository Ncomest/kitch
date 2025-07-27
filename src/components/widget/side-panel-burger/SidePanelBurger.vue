<script setup>
import TheLink from "@components/shared/link/the-link/TheLink.vue";
import { useSidePanel } from "@stores/side-panel";

const sidePanel = useSidePanel();
</script>
<template>
  <div class="side-panel-burger">
    <TheLink text="Заказать" href="#post-order" @click="sidePanel.close()"/>
    <TheLink text="Каталог" href="#catalog-kitchen" @click="sidePanel.close()"/>
    <TheLink text="О нас" href="#about-us" @click="sidePanel.close()"/>
  </div>
</template>
<style src="./style.scss"></style>
