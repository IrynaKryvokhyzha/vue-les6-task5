<template>
  <div class="container">
    <div class="item">
      <a :href="cardData.link" class="link">
        <div class="image">
          <img :src="cardData.imgSrc" alt="image" />
        </div>
        <div class="title">
          <h3>{{ cardData.title }}</h3>
        </div>
        <div class="price">{{ cardData.price }} ₴</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",

  props: {
    cardData: {
      type: Object,
      default: () => ({}),
    },
  },
};
</script>

<style lang="scss" scoped></style>
