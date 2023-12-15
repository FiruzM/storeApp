<template>
  <div>
    <h2 class="py-4 font-semibold text-xl">Products</h2>
    <ul v-if="pending" class="grid grid-cols-4 gap-4">
      <li v-for="p in 20">
        <Skeleton class="w-full h-52" />
      </li>
    </ul>
    <ul v-else class="grid grid-cols-4 gap-4">
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
const { data: products, pending } = await useFetch("https://fakestoreapi.com/products", {
  lazy: true
});
</script>

<style lang="scss" scoped></style>
