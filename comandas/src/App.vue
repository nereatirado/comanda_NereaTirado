<script setup lang="ts">
import currency from "@/components/Currency.vue";
import { ref } from "vue";
const text = ref('')

</script>

<template>
  <div class="principalComponente">
    <h1>{{ text }}</h1>
    <input v-model="text">
    <!-- Aqui hacemos que el boton muestre un alert confome se ejecutado -->
    <button onclick="alert('Your order has been placed!');">Place order</button>
  </div>
  <currency></currency>
</template>

<style scoped>
.principalComponente{
  text-align: center;
  margin-top: 250px;
}
</style>
