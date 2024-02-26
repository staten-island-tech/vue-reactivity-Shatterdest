<script setup>
import { useRoute } from "vue-router";

const route = useRoute();

const props = defineProps(["table"]);
const table = props.table;
const elements = table.elements;
const element = table.elements[route.params.number - 1];
</script>

<template>
  <div>
    <router-link to="/">Go Back</router-link>
    <h1>{{ element }}</h1>
    <h1>Element Name: {{ element.name }}</h1>
    <h2>Element #: {{ element.number }}</h2>
    <h2>Appearance: {{ element.appearance }}</h2>
    <h2>Atomic Mass: {{ element.atomic_mass }}</h2>
    <img :src="element.bohr_model_image" alt="">
  </div>
</template>

<style scoped>
.hi {
  background-color: green;
}
</style>
