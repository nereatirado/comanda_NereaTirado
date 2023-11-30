<script setup lang="ts">
import Currency from "@/components/Currency.vue";
import Comanda from "@/components/Comanda.vue"
import { ref } from "vue";

const text = ref('')
const comidas = [
  { name: "Hamburger 🍔.", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 }

]
</script>

<template>
  <div class="principalComponente">
    <h1>{{ text }}</h1>
    <input v-model="text">
    <!-- Aqui hacemos que el boton muestre un alert confome se ejecutado -->
    <button onclick="alert('Your order has been placed!');">Place order</button>
  </div>
  <Currency></Currency>

  <Comanda v-for="comida in comidas" :key="comida.name" :comer="comida"></Comanda>
</template>

<style scoped>
.principalComponente {
  text-align: center;
  margin-top: 250px;
}
</style>
