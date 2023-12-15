<template>
  <div>
    <h2 class="py-4 font-semibold text-xl">Products</h2>

    <ul class="grid grid-cols-4 gap-4">
      <li v-for="p in products">
        <ProductCard :product="p" />
      </li>
    </ul>
  </div>
</template>

<script setup>

definePageMeta({
  layout: "products",
}); //Для отоброжения другого лейаута

// fetch products
const { data: products } = await useFetch("https://fakestoreapi.com/products");
</script>

<style lang="scss" scoped></style>
