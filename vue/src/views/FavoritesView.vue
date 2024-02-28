<template>
  <div>
    <router-link to="/">Go Back</router-link>
    <h1
      v-for="item in favoriteElements"
      :key="item"
      @click="openElementView(item.number)"
    >
      {{ item.name }}
    </h1>
  </div>
</template>

<script setup>
import { favorites } from "../assets/favorites";
import { pTable } from "@/assets/table";
import router from "@/router";

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

<style scoped></style>
