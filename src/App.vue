<template>
  <div class="main-container">
    <h1>{{ orderTitle }}</h1>
    <section>
      <input v-model="orderTitle" type="text" />
      <button @click="completeOrder" type="button">Complete Order</button>
    </section>
  </div>

  <CurrencyComponent></CurrencyComponent>

  <header>
    <h1>{{ itemName }}</h1>
    <section>
      <input v-model="itemName" type="text" />
      <button @click="addToCart" type="button">Add to Cart</button>
    </section>
  </header>

  <main>
    <div>
      <label for="selectedCurrency">Currency</label>
      <select v-model="selectedCurrency" name="selectedCurrency" id="selectedCurrency">
        <option value="€">EUR (€)</option>
        <option value="£">GBP (£)</option>
      </select>
    </div>

    <section class="products">
      <OrderItem
        v-for="(product, index) in foodItems"
        :info="product"
        :key="index"
        @add-to-cart="addToCart"
      />
    </section>
  </main>
</template>

<script setup>
import { ref, provide } from "vue";
import type { Currency } from "./types/Currency";
import type Product from "./types/Product";
import CurrencyComponent from "@/components/Currency.vue";
import OrderItem from "./components/Comanda.vue";

const orderTitle = ref("My Delicious Order");
const selectedCurrency = ref("€");
const foodItems = ref<Product[]>([
  { name: "Yummy Burger 🍔.", price: 5 },
  { name: "Cheesy Delight 🧀", price: 6 },
  { name: "Impossible Delight 🥕", price: 7 },
  { name: "Crispy Fries 🍟", price: 2 },
]);
const cart = ref<Product[]>([]);

const addToCart = (product: Product): void => {
  cart.value.push(product);
  alert(`Added ${product.name} to the cart!`);
};

const completeOrder = (): void => {
  cart.value = [];
  alert(`Your order ${orderTitle.value} has been completed.`);
};

provide("selectedCurrency", selectedCurrency);
</script>

<style scoped>
.main-container {
  text-align: center;
  margin-top: 250px;
}

header,
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
}

.products {
  align-items: flex-start;
}

main {
  margin-top: 25px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

div {
  display: flex;
  gap: 5px;
}
</style>
