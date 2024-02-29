<template>
  <main class="">
    <router-link class="button" to="/">Home</router-link>
    <button id="favorite-button" class="button" @click="openFavoritesView()">Favorites</button>
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
import ElementView from "../views/ElementView.vue";
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
#periodic-table {
  display: grid;
  grid-template-columns: repeat(18, auto) 1fr;
  gap: 0.1vw;
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
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
  color: rgb(190, 190, 190)
}
.button:hover {
  color: black;
  background-color: white;
}
</style>
