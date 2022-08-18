<template>
  <h1 class="text-h4 category">Product Category: {{ getCategoryName }}</h1>
  <div class="flex wrap justify-center q-mb-xl">
    <div :key="index" v-for="(product, index) of products">
      <single-product
        :name="product['name']"
        :image="product['image']"
        :price="product['price']"
        :rating="product['rating']"
        :amount="product['amount']"
        :badges="product['badges']"
        :addedToWishList="product['added-to-wishlist']"
      />
    </div>
  </div>
</template>

<style></style>

<script>
import SingleProduct from "@/components/SingleProduct";
export default {
  name: "CategoryProducts",
  components: { SingleProduct },
  props: {
    products: {
      type: Object,
      required: true,
    },
    category: {
      type: String,
      required: true,
    },
  },
  computed: {
    getCategoryName() {
      return this.category.replaceAll("-", " ");
    },
  },
};
</script>
<style lang="scss" scoped>
.category {
  text-align: center;
  text-transform: capitalize;
  color: dodgerblue;
}
</style>
