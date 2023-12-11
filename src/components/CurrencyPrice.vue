<script setup>
import { computed, defineProps, inject } from "vue";
import type { Currency as CurrencyType } from "@/types/Currency";

const componentProps = defineProps<{
  originalPrice: number;
}>();

const currency: CurrencyType | undefined = inject("selectedCurrency");

const convertedPrice = computed(() => {
  if (currency) {
    switch (currency) {
      case "€":
        return componentProps.originalPrice;
      case "£":
        return (componentProps.originalPrice * 0.86).toFixed(2);
      default:
        return componentProps.originalPrice;
    }
  } else {
    return componentProps.originalPrice;
  }
});

const formattedPrice = computed(() => {
  return `${convertedPrice.value}${currency || ""}`;
});
</script>

<template>
  <span>{{ formattedPrice }}</span>
</template>
