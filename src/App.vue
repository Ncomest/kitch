<script setup>
import TheHome from "@components/pages/home/TheHome.vue";
import TheHeader from "@components/widget/header/TheHeader.vue";
import SidePanelBurger from "@components/widget/side-panel-burger/SidePanelBurger.vue";
import SidePanel from "@components/shared/side-panel/SidePanel.vue";
import { useSidePanel } from "./stores/side-panel";
import TheFooter from "./components/widget/footer/TheFooter.vue";


const sidePanel = useSidePanel();

</script>

<template>
  <TheHeader />
  <transition name="slide">
    <SidePanel
      v-if="sidePanel.burger.isOpen"
      class="app-side-panel__burger-wrapper"
    >
      <SidePanelBurger />
    </SidePanel>
  </transition>

  <TheHome />

  <TheFooter />
</template>

<style src="./style.scss"></style>
