<template>
  <div>
    <ProductDetails :product="product" />
  </div>
</template>

<script setup>
const { id } = useRoute().params;
const url = `https://fakestoreapi.com/products/${id}`

//fetching

const {data:product} = await useFetch(url, {key: id})
definePageMeta({
  layout: "products",
}); //Для отоброжения другого лейаута
</script>

<style scoped></style>
