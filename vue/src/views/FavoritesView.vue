<template>
  <div>
    <NavBar />
    <Element
      v-for="element in favoriteElements"
      :key="element.number"
      :element="element"
      @click="openElementView(element.number)"
    />
  </div>
</template>

<script setup>
import { favorites } from "../assets/favorites";
import { pTable } from "@/assets/table";
import router from "@/router";
import Element from "@/components/Element.vue";
import NavBar from "@/components/NavBar.vue";

const favoriteElements = [];
pTable.elements.forEach((element) => {
  if (favorites.value.includes(element.number)) {
    favoriteElements.push(element);
  }
});

const openElementView = function (i) {
  router.push({ name: "element", params: { number: i } });
};
</script>

<style scoped>
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
  z-index: 500;
}
</style>
