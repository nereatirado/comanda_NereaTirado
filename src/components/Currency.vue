<template>
    <div class="segundoComponente">
      <span>Currency</span>
      <select v-model="selectedCurrency">
        <option value="usd">Dollars($)</option>
        <option value="eur">Euros(€)</option>
      </select>
    </div>
  </template>
  
  <script setup>

  </script>
  

<style scoped>
.segundoComponente{
    text-align: center;
    margin-top: 10px;
}
select{
    margin-left: 10px;
}
</style>