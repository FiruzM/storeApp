<template>
  <div>
    <div
      v-if="products == '[]'"
      class="flex justify-center font-extrabold text-5xl uppercase py-11"
    >
      <p class="text-[#12b488]">you have not added items to your cart</p>
    </div>

    <ul v-else class="flex flex-col gap-10">
      <li
        v-for="product in parsedProducts"
        class="flex justify-between items-center border rounded-lg p-5"
      >
        <img :src="product.image" alt="product image" class="w-9" />
        <p class="font-semibold text-[#12b488]">{{ product.title }}</p>
        <p>Amount: {{ product.amount }}</p>
      </li>
    </ul>
    <div>
      <p class="pt-5 font-bold">Totla Price: {{ totalPrice }}$</p>
    </div>
  </div>
</template>

<script setup>
import { useStorage } from "@vueuse/core";

const products = useStorage("cart", "[]");
const parsedProducts = computed(() => JSON.parse(products?.value));

const totalPrice = computed(()=>{
  return parsedProducts.value.reduce((acc, curr) => acc + (curr.price * curr.amount), 0).toFixed(2)
})
console.log(totalPrice.value);
</script>

<style lang="scss" scoped></style>
