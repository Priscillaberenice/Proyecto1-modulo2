<template>
  <div v-if="product" class="bg-gray-200 shadow-md rounded-lg max-w-xs mt-5 border border-gray-600 hover:border-emerald-800 hover:shadow-lg transition-all duration-300 p-4 mb-10 ml-10">
    <h2 class="text-xl font-bold text-green-950 font-sans mb-4">{{ product.title }}</h2>
    <p class="text-gray-700 mb-4 font-sans font-semibold text-xl">{{ product.description }}</p>
    <button @click="getProduct" class="box-decoration-clone hover:box-decoration-slice bg-gradient-to-r from-indigo-600 to-pink-500 text-white px-2 text-lg font-sans font-semibold p-2 bg-white shadow-md rounded-lg overflow-hidden mt-2 border border-gray-300 hover:border-emerald-800 hover:shadow-lg transition-all duration-300">I WANT IT🫵</button>
  </div>
  </template>
  
  <script>
  export default {
    name: "ProductDetails",
    props: ["product"],
    methods: {
      getProduct() {
        this.$emit('getProduct', this.product);
      }
    }
  };
  </script>