<template>
  <div class="bg-gradient-to-r from-gray-600 via-gray-400 to-gray-200 min-h-screen flex flex-col">
    <h1 v-if="!selectedProduct && !productCard" class="text-5xl text-green-950 underline decoration-emerald-800 font-mono font-semibold text-center mt-10">
      {{ title }}
    </h1>
    <div class="flex-grow flex justify-center items-center"> 
    <ProductList v-if="!selectedProduct" @productSelected="fetchProductDetails" />
    <ProductDetails v-if="selectedProduct" :product="selectedProduct" @getProduct="showProductCard" />
    <ProductCard v-if="productCard" :product="productCard" />
    </div>
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import ProductDetails from './components/ProductDetails.vue';
import ProductCard from './components/ProductCard.vue';

export default {
  name: "App",
  components: {
    ProductList,
    ProductDetails,
    ProductCard
  },
  data() {
    return {
      title: "Fake Store API",
      selectedProduct: null,
      productCard: null,
      showTitle: true,
    };
  },
  methods: {
    fetchProductDetails(productId) {
      fetch("https://fakestoreapi.com/products/" + productId)
        .then(response => response.json())
        .then(data => {
          this.selectedProduct = data;
          this.productCard = null;
        });
    },
    showProductCard(product) {
      this.productCard = product;
    }
  }
};
</script>

