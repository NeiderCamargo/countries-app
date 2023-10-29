<script setup lang="ts">
import pageHeader from './components/pageHeader.vue';
import axiosClient from "./utils/axios";
import { onMounted } from 'vue';

//función para consultar los paises
const fetchCountries = async ()=>{
  const {data} = await axiosClient.get("/all")
  
};

//ejecutar función
fetchCountries();
onMounted(()=>{
  fetchCountries();
})
</script>

<template>
  <!--Con esto llamamos al template del archico pageheader-->
  <pageHeader/>
</template>
