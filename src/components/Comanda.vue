<template>
    <p>{{ comida.name }}</p>
    <p>{{ comida.price }}</p>
</template>

<script setup lang="ts">
// utilizamos del defineProps para definir las propiedades que define del componente
const {comida} = defineProps(['comida'])
</script>