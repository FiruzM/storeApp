<template>
  <div>
    <header class="shadow-sm bgg-white">
      <nav class="container mx-auto p-4">
        <ul class="flex gap-5">
          <li>
            <NuxtLink to="/">Home</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/about">About</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/products" class="btn">Products</NuxtLink>
          </li>
        </ul>
      </nav>
    </header>

    <div class="container mx-auto p-4">
      <slot />
    </div>
  </div>
</template>

<script setup></script>

<style>
.router-link-exact-active {
  color: #12b488;
}
</style>
