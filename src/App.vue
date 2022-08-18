<template>
  <q-layout view="lHh Lpr lFf">
    <category-products
      :key="category"
      :category="category"
      :products="appendProducts(categoryProducts)"
      v-for="[category, categoryProducts] of Object.entries(products)"
    />
  </q-layout>
</template>

<script>
import axios from "axios";
import CategoryProducts from "@/components/CategoryProducts";

export default {
  name: "LayoutDefault",
  components: { CategoryProducts },
  data() {
    return {
      products: {},
    };
  },
  methods: {
    appendProducts(products) {
      return Array.isArray(products) ? products : [products];
    },
  },
  mounted() {
    const urlApi = "http://127.0.0.1:8082/products";
    axios
      .get(urlApi)
      .then((resp) => {
        this.products = resp.data;
      })
      .catch((err) => console.log("Can not fetch products", err));
  },
};
</script>
