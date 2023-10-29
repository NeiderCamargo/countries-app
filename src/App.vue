<script setup lang="ts">
import pageHeader from './components/pageHeader.vue';
import axiosClient from "./utils/axios";
import { onMounted, ref} from 'vue';
import {Country} from "./models/country.model";

//variable de estado
const countries=ref<Country[]>([]);//constante que guarda un estado de los países

//función para consultar los paises
const fetchCountries = async ()=>{
  try{
    const {data} = await axiosClient.get("/all")
    countries.value=data;
  }catch(error){//mensaje por si hay algun error
    console.log(error)
  }
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
  <div v-for="country in countries">{{ country.name.common}}</div>
</template>
