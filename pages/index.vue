<template>
  <div class="grid grid-cols-4 gap-4">
    <div v-if="products" v-for="(product, index) in products" :key="index">
      <ProductComp :product="product"/>
    </div>
  </div>
</template>

<script setup lang="ts">
const {data: products} = await useFetch('/api/products')
</script>

<style scoped>

</style>