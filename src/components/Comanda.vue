<script setup>
import type ProductType from "@/types/Product";
import type { Currency as CurrencyType } from "@/types/Currency";
import CurrencyPriceComponent from "./CurrencyPrice.vue";

const componentProps = defineProps<{
  productInfo: ProductType;
}>();

const componentEmits = defineEmits<{
  addToCart: [productInfo: ProductType];
}>();
</script>

<template>
  <article>
    <p>{{ productInfo.name }}</p>
    <CurrencyPriceComponent :originalPrice="productInfo.price" />
    <button @click="onAddToCart" type="button">
      Add to Cart
    </button>
  </article>
</template>

<style scoped>
article {
  display: flex;
  gap: 5px;
  flex-wrap: wrap;
}
</style>
