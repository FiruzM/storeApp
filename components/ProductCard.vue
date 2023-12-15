<template>
  <div class="card text-center flex flex-col justify-between">
    <img :src="product.image" alt="product thumb" class="thumb" />
    <p class="font-bold text-gray-500 m-4 truncate">{{ product.title }}</p>
    <NuxtLink :to="`/products/${product.id}`">
      <p class="btn my-4">View Details</p>
    </NuxtLink>
    <div v-if="!isAdded" class="flex items-center gap-5">
      <button class="btn px-8" @click="addProduct">Add</button>
      <button class="btn px-5" @click="decrement">-</button>
      <span class="border px-8 py-1 rounded-lg border-[#12b488]">{{
        amount
      }}</span>
      <button class="btn px-5" @click="increment">+</button>
    </div>
    <div v-else>
      <button @click="deleteProduct" class="btn">Delete</button>
    </div>
  </div>
</template>

<script setup>
import { useStorage } from "@vueuse/core";

const { product } = defineProps(["product"]);
const products = useStorage("cart", '[]');

const parsedProducts = computed(() => JSON.parse(products?.value));

let amount = ref(1);

function increment() {
  amount.value++;
}

function decrement() {
  if (amount.value == 1) {
    return (amount.value = 0);
  }
  amount.value--;
}

function deleteProduct() {
  const filteredProduct = parsedProducts.value.filter(
    (p) => p.id !== product.id
  );

  products.value = JSON.stringify(filteredProduct);
}

const isAdded = computed(() => {
  const currentProduct = parsedProducts.value.find((p) => p.id === product.id);
  if (currentProduct) {
    return true;
  }
  return false;
});

watchEffect(() => {
  console.log(isAdded.value);
});

function addProduct() {
  const productWithAmount = {
    ...product,
    amount: amount.value,
  };
  
  if (parsedProducts.value.length) {
    products.value = JSON.stringify([...parsedProducts.value, productWithAmount])
  } else {
    products.value = JSON.stringify([productWithAmount])
  }
}
</script>

<style lang="scss" scoped></style>
