<template>
  <q-card class="product">
    <img :src="image" />
    <q-card-section class="flex column">
      <span class="text-h6">{{ name }}</span>
      <span class="text-subtitle1">Current Price: {{ price["current"] }}</span>
      <span class="text-subtitle2">
        Regular Price: <s>{{ price["regular"] }}</s>
      </span>
      <span class="text-subtitle2">Amount: {{ amount }}</span>
      <span class="text-subtitle2">Rating: {{ rating }}</span>
      <q-badge
        class="product__badge-wish text-subtitle2 q-mt-md"
        v-if="addedToWishList"
        color="orange"
        label="Added To Wish List!"
      />
      <div class="q-mt-md">
        <q-badge
          :key="category"
          v-for="[category, value] of Object.entries(badges)"
          v-show="value"
          color=" q-mr-lg primary text-subtitle2"
        >
          {{ category }}
        </q-badge>
      </div>
    </q-card-section>
  </q-card>
  <q-tooltip anchor="center middle" self="top middle">
    <p class="text-subtitle1">Add to Wish List!</p>
  </q-tooltip>
</template>

<style></style>

<script>
export default {
  name: "SingleProduct",
  props: {
    addedToWishList: {
      type: Boolean,
      required: true,
    },
    amount: {
      type: Number,
      required: true,
    },
    badges: {
      type: Object,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    price: {
      type: Object,
      required: true,
    },
    rating: {
      type: Number,
      required: true,
    },
  },
};
</script>
<style lang="scss" scoped>
.product {
  min-height: 480px;
  &__badge-wish {
    width: min-content;
  }
  margin: 24px;
  width: 350px;
  &__tooltip {
    font-size: 1.5rem !important;
  }
  &:hover {
    background-color: silver;
    opacity: 0.75;
    cursor: pointer;
  }
}
</style>
