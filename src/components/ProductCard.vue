<template>
  <div v-if="product" class="bg-gray-200 shadow-md rounded-lg max-w-xs ml-10 mt-10 mb-10 border border-gray-600 hover:border-emerald-800 hover:shadow-lg transition-all duration-300 p-4">
    <img :src="product.image" alt="Product Images" class="w-full h-full object-contain mb-4" />
    <p class="text-2xl text-gray-700 mb-4 font-sans font-semibold">${{ product.price }}</p>
    <a :href="'https://fakestoreapi.com/'" class="box-decoration-clone hover:box-decoration-slice bg-gradient-to-r from-indigo-600 to-pink-500 text-white px-2 text-sm font-sans font-semibold p-2 rounded-lg bg-white shadow-md overflow-hidden mt-10 border border-gray-300 hover:border-emerald-800 hover:shadow-lg transition-all duration-300">ADD TO CART🎁</a>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: ['product']
};
</script>
  