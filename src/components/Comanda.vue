<template>
    <p>{{ comida.name }}</p>
    <p>{{ comida.price }}</p>
    <button>Add to Cart</button>
</template>

<script setup lang="ts">
// utilizamos del defineProps para definir las propiedades que define del componente
const {comida} = defineProps(['comida'])
</script>

<style>
p{
    display: inline-block;
    margin-left: 15px;
}
button{
    margin-left: 5px;
}
</style>