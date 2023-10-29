<script setup lang="ts">
import {defineProps} from "vue";

interface Props{
    countries: Country[];   
}

defineProps<Props>();
</script>

<template>
    <!--Forma en que se muestra las tarjetas-->
    <div class="grid grid-cols-1" sm:grid-2 md:grid-cols-3 gap3></div>
    <div v-for="country in countries" class="border border-gray-300 rounded p-3">{{ country.name.common }}</div>
</template>