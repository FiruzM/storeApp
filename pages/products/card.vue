<template>
  <div>
    <ul class="flex flex-col gap-10">
      <li v-for="product in parsedProducts" class="flex items-center justify-between">
        <img :src="product.image" alt="product image" class="w-9" />
        <p class="font-semibold text-[#12b488]">{{ product.title }}</p>
        <p>Amount: {{ product.amount }}</p>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { useStorage } from "@vueuse/core";

const products = useStorage("cart", "[]");
const parsedProducts = computed(() => JSON.parse(products?.value));
</script>

<style lang="scss" scoped></style>
