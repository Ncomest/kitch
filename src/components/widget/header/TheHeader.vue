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
      <TheLink text="Заказать" href="#post-order" />
      <TheLink text="Каталог" href="#catalog-kitchen" />
      <TheLink text="О нас" href="#about-us" />
    </nav>
    <TheBurger
      class="the-header__burger"
      @click="burger.toggle()"
      v-if="!burger.isOpen"
    />
    <!-- <button
      class="the-header__cross-close"
      @click="burger.close()"
      v-if="burger.isOpen"
    >
      <span>
        <svg
          width="18"
          height="18"
          viewBox="0 0 18 18"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M1 1.24459L16.7554 17M1 16.7554L16.7554 1"
            stroke="black"
            stroke-width="1.5"
          />
        </svg>
      </span>
    </button> -->
  </div>
</template>
<style src="./style.scss"></style>
