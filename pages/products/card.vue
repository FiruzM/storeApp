<template>
  <div>
    <div v-if="products == '[]'" class="flex justify-center font-extrabold text-5xl uppercase py-11">
      <p class="text-[#12b488]">you have not added items to your cart</p>
    </div>

    <ul v-else class="flex flex-col gap-10">
      <li
        v-for="product in parsedProducts"
        class="flex items-center justify-between"
      >
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
