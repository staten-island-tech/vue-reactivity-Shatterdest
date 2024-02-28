<template>
  <main class="">
    <button id="favorite-button" @click="openFavoritesView()">Favorites</button>
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
#periodic-table {
  display: grid;
  grid-template-columns: repeat(18, auto) 1fr;
  gap: 0.1vw;
}
#favorite-button {
  font-size: 2.5rem;
  border: white solid 5px;
  border-radius: 15px;
}
</style>
