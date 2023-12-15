<template>
  <div>
    <header class="shadow-sm bg-white">
      <nav class="container mx-auto p-4">
        <ul class="flex items-center gap-10">
          <li class="font-bold text-[#12b488]">
            <NuxtLink to="/">StoreApp</NuxtLink>
          </li>
          <li class="relative">
            <NuxtLink to="/products/card">
              <img src="../assets/img/card.png" alt="icon" class="w-[40px]" />
              <div
                class="absolute rounded-full bg-red-700 top-5 left-6 text-white flex justify-center items-center w-[25px]"
              >
                {{ totalAmounts }}
              </div>
            </NuxtLink>
          </li>
        </ul>
      </nav>
    </header>

    <div class="container mx-auto p-4">
      <slot />
    </div>

    <footer class="bg-[#12b488]">
      <div class="flex justify-center">
        <p class="py-4 text-2xl">What are you looking for ?</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { useStorage } from "@vueuse/core";
const products = useStorage("cart", '[]');
const parsedProducts = computed(() => JSON.parse(products?.value));

const totalAmounts = computed(()=> {
  return parsedProducts.value.reduce((acc, curr) => acc + curr.amount, 0)
})

</script>

<style>
.router-link-exact-active {
  color: #12b488;
}
</style>
