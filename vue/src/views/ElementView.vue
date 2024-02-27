<script setup>
import { useRoute } from "vue-router";
import { favorites } from "../assets/favorites.js"

const route = useRoute();

const props = defineProps(["table"]);
const table = props.table;
const elements = table.elements;
const element = table.elements[route.params.number - 1];



function toggleFavorite() {
  if (favorites.value.includes(element.name)) {
    favorites.value.splice(favorites.value.indexOf(element.name), 1)
    console.log(favorites.value)
  } else {
    favorites.value.push(element.name)
    console.log(favorites.value)
  }
}
</script>

<template>
  <div class="">
    <router-link to="/">Go Back</router-link>
<button @click="toggleFavorite">favorite</button>
    <h1>{{ element }}</h1>
    <h1>Element Name: {{ element.name }}</h1>
    <h2>Element #: {{ element.number }}</h2>
    <h2>Appearance: {{ element.appearance }}</h2>
    <h2>Atomic Mass: {{ element.atomic_mass }}</h2>
    <img :src="element.bohr_model_image" alt="" />
  </div>
</template>

<style scoped>

</style>
