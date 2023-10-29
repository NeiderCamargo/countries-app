<script setup lang="ts">
import pageHeader from './components/pageHeader.vue';
import axiosClient from "./utils/axios";
import { onMounted, ref} from 'vue';
import {Country} from "./models/country.model";
import CountryList from "./components/CountryList.vue";

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
  <div class="container max-w-screen-lg mx-auto px-6">
    <CountryList :countries="countries"/>
  </div>
  
</template>
