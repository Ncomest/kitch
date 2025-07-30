<script setup>
import MainSlider from "@components/widget/slider/main-slider/MainSlider.vue";
import OurDesigner from "@components/section/ourDesigner/OurDesigner.vue";
import OurReviews from "@components/section/ourReviews/OurReviews.vue";
import CatalogKitchen from "@components/shared/grid/catalog-kitchen/CatalogKitchen.vue";
import KitchenForm from "@components/widget/forms/kitchen-form/KitchenForm.vue";
import TheContainer from "@components/shared/container/TheContainer.vue";
</script>
<template>
  <main class="the-home">
    <MainSlider class="the-home__main-slider" />
    
    <TheContainer title="Каталог кухонь">
      <CatalogKitchen />
    </TheContainer>
    
    <TheContainer title="Наши дизайнеры">
      <OurDesigner />
    </TheContainer>

    <TheContainer title="Отзывы">
      <OurReviews />
    </TheContainer>

    <TheContainer title="Сделать заявку">
      <KitchenForm />
    </TheContainer>
  </main>
</template>
<style src="./style.scss"></style>
