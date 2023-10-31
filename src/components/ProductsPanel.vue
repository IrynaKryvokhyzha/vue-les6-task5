<template>
  <div class="card-panel">
    <product-card
      v-for="card in cardsListData"
      :key="card.id"
      :card-data="card"
    />
  </div>
</template>

<script>
import ProductCard from "./ProductCard.vue";
export default {
  name: "ProductsPanel",

  props: {
    cardsListData: {
      type: Array,
      default: () => [],
    },
  },
  components: {
    ProductCard,
  },
};
</script>

<style lang="scss" scoped></style>
