<script setup lang="ts">
import type Product from "../types/Product.ts";
defineProps<{
  info: Product;
}>();

defineEmits<{
  "@añadirProducto": [info: Product];
}>();
</script>

<template>
  <div class="producte">
    <span class="name">{{ info.name }}</span>
    <span class="price">{{ info.price }}</span>
    <button @click="$emit('@añadirProducto', info)" type="button">Add to Cart</button>
  </div>
</template>

<style scoped>
.producte {
  display: flex;
  text-align: center;
  margin: 10px;
}

.name {
  margin-right: 10px;
}

.price {
  margin-right: 10px;
}
</style>
