<script setup>
import { useRoute } from "vue-router";
import { favorites } from "../assets/favorites.js";
import { ref } from "vue";
import NavBar from "@/components/NavBar.vue";

const route = useRoute();

const props = defineProps(["table"]);
const table = props.table;
const element = table.elements[route.params.number - 1];
const favorited = ref(false);

if (favorites.value.includes(element.number)) {
  favorited.value = true;
} else {
  favorited.value = false;
}

const toggleFavorite = function () {
  if (favorites.value.includes(element.number)) {
    favorites.value.splice(favorites.value.indexOf(element.number), 1);
    console.log(favorites.value);
    favorited.value = false;
  } else {
    favorites.value.push(element.number);
    console.log(favorites.value);
    favorited.value = true;
  }
};
</script>

<template>
  <div class="container">
    <NavBar/>
    <button v-if="favorited" class="button" @click="toggleFavorite()">
      Favorited!
    </button>
    <button v-else class="button" @click="toggleFavorite()">Favorite!</button>
    <!-- <h1>{{ element }}</h1> -->
    <h1 class="title">{{ element.name }}, #{{ element.number }}</h1>
    <h2>Atomic Mass: {{ element.atomic_mass }}</h2>
    <h2>Appearance: {{ element.appearance }}</h2>
    <h2>Category: {{ element.category }}</h2>
    <h2>Electron configuration: {{ element.electron_configuration }}</h2>
    <h2>Block: {{ element.block.toUpperCase() }}</h2>
    <h2>Description: {{ element.summary }}</h2>
    <img :src="element.bohr_model_image" :alt="element.name" />
  </div>
</template>

<style scoped>

.container {
  height: 100vh;
  width: 100vw;
}
.title {
  font-size: 5rem;
  text-align: center;
}
.button {
  font-size: 2.5rem;
  border: white solid 5px;
  border-radius: 15px;
  margin-bottom: 1rem;
  margin-left: 10rem;
  margin-top: 5rem;
  padding: 1rem 1rem;
  transition: 0.3s all;
  color: rgb(190, 190, 190);
}
.button:hover {
  color: black;
  background-color: white;
}

img {
  height: auto;
  width: 30vw;
  margin: 1rem auto;
}
</style>
