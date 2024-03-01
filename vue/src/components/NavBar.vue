<template>
    <div class="container">
        <router-link class="button" to="/">Home</router-link>
      <button id="favorite-button" class="button" @click="openFavoritesView()">
        Favorites
      </button>
    </div>
</template>

<script setup>
import { useRouter } from "vue-router";
const router = useRouter();


const openFavoritesView = function () {
  router.push("/favorites");
};
</script>

<style lang="css" scoped>
.container {
}
.button {
    color:white;
    font-size: 3rem;
    transition: 0s all;
}

.button:hover {
    color: black;
    background-color: white;
}
</style>