<template>
  <section>
    <section
      v-for="product in productsList"
      :key="product.id"
      class="products"
    >
      <productCard :product="product" @click="showProductDetails(product)" />
    </section>
    <ProductDetails
      :isShowProductDetails="isShowProductDetails"
      :product="clickedProduct"
    />
  </section>
</template>

<script>
import ProductCard from "./productCard.vue";
import { mapState, mapMutations } from "vuex";
import productsList from "../../data/productsList";
import ProductDetails from "./ProductDetails.vue";

export default {
  name: "ProductsPage",
  components: { ProductCard, ProductDetails },
  data() {
    return {
      clickedProduct: null,
    };
  },
  computed: {
    ...mapState(["productsList", "isShowProductDetails", "cart", "productIsInCart"]),
  },
  methods: {
    changeIsShowProductDetails() {
      this.$store.commit("CHANGE_IS_SHOW_PRODUCT_DETAILS");
    },
    showProductDetails(product) {
      this.changeIsShowProductDetails();
      this.clickedProduct = product;
    },
  },
};
</script>

