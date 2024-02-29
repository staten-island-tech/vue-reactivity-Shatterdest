<template>
  <main class="">
    <h1 class="title">The Periodic Table of Vuelements</h1>
    <div class="container">
      <router-link class="button" to="/">Home</router-link>
      <button id="favorite-button" class="button" @click="openFavoritesView()">
        Favorites
      </button>
    </div>
    <section id="periodic-table">
      <Element
        v-for="element in elements"
        :key="element.number"
        :element="element"
        :style="{ 'grid-column': element.xpos, 'grid-row': element.ypos }"
        @click="openElementView(element.number)"
      />
    </section>
    <h1>{{ favorites.value }}</h1>
  </main>
</template>

<script setup>
import Element from "./Element.vue";
import { useRouter } from "vue-router";
import { favorites } from "../assets/favorites.js";
const props = defineProps(["table"]);
const table = props.table;
const elements = table.elements;

const router = useRouter();

const openElementView = function (i) {
  router.push({ name: "element", params: { number: i } });
};

const openFavoritesView = function () {
  router.push("/favorites");
};
</script>

<style lang="css" scoped>
main {
  height: 100vh;
  width: 100vw;
}

.title {
  font-size: 5vw;
  color: white;
  text-align: center;
  margin-right: 10%;
}
#periodic-table {
  display: grid;
  grid-template-columns: repeat(18, auto) 1fr;
  gap: 0.1vw;
  margin: 0;
  top: 50%;
  left: 50%;
}

.container {
  margin: 0 auto;
}
.button {
  font-size: 2.5rem;
  border: white solid 5px;
  border-radius: 15px;
  padding: 1rem 1rem;
  transition: 0.3s all;
  color: rgb(190, 190, 190);
}
.button:hover {
  color: black;
  background-color: white;
}
</style>
