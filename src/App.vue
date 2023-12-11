<script setup lang="ts">
import { ref, type Ref, reactive } from "vue";
import Currency from "@/components/Currency.vue"
import type Product from "./types/Product.ts";
import Comanda from "./components/Comanda.vue";
const nombreComanda = ref('');
const comidas = reactive([
  { name: "Hamburger 🍔", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 },
]);

const comidasComanda: Ref<Product[]> = ref([]);

function añadirComida(product: Product) {
  comidasComanda.value.push(product);
  alert(comidasComanda.value.map((product) => product.name));
}

function placeOrder() {
  alert('Your order has been placed!');
  comidasComanda.value = [];
}
</script>

<template>
  <div class="principal">

    <h1>{{ nombreComanda }}</h1>
    <input v-model="nombreComanda" type="text" /><br>
    <button @click="placeOrder" type="button" class="separar">Place Order</button>
    <br>

    <Currency class="currency"></Currency>

    <ul>
    <li v-for="(product, index) in comidas" :key="index">
      <div class="centrar">
        <Comanda @@afegirProducteComanda="(product: Product) => añadirComida(product)" :info="product" />
      </div>
    </li>
  </ul>
  </div>
</template>

<style scoped>
.principal {
  text-align: center;
}

ul, li {
  list-style-type: none;
  text-align: center;
}

.separar {
  margin: 20px;
}

.centrar {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
</style>