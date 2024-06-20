<template>
    <div>
        <div class="flex justify-start mb-2 mt-10 ml-2">
          <h2 class="box-decoration-clone hover:box-decoration-slice bg-gradient-to-r from-indigo-600 to-pink-500 text-white px-2 text-3xl font-sans font-semibold">
            Special Prices✨
          </h2>
        </div>
      <ul class="grid grid-cols-6 gap-4 mt-5 mb-10">
        <li v-for="product in products" :key="product.id" class="block w-full text-center box-decoration-clone hover:box-decoration-slice bg-gradient-to-r from-indigo-600 to-pink-500 text-white px-2 text-lg font-sans font-semibold p-2 bg-white shadow-md rounded-lg overflow-hidden mt-2 border border-gray-300 hover:border-emerald-800 hover:shadow-lg transition-all duration-300">
            <div class="bg-gray-200 shadow-md rounded-lg p-4 border border-gray-600 hover:border-emerald-800 hover:shadow-lg transition-all duration-300 w-64 h-80 mx-auto"> 
            <img :src="product.image" alt="Product Images" class="w-full h-32 mx-auto mb-4 object-contain" />
            <p class="text-emerald-800 font-sans font-semibold text-sm">{{ product.title }}</p>
            <button @click="selectProduct(product.id)" class="box-decoration-slice hover:box-decoration-slice bg-gradient-to-r from-pink-500 to-emerald-600 text-white px-2 text-lg font-sans font-semibold p-2 bg-white shadow-md rounded-lg overflow-hidden mt-2 border border-gray-300 hover:border-emerald-800 hover:shadow-lg transition-all duration-300">
              SEE DETAILS➕
            </button>
            </div>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: "ProductList",
    data() {
      return {
        products: [],
      };
    },
    created() {
      fetch("https://fakestoreapi.com/products")
        .then(response => response.json())
        .then(data => {
          this.products = data;
        });
    },
    methods: {
      selectProduct(productId) {
        this.$emit('productSelected', productId);
      }
    }
  };
  </script>