<template>
  <div class="container">
    <router-link class="button" to="/">Home</router-link>
    <router-link class="button" to="/favorites">Favorites</router-link>
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";
const router = useRouter();


</script>

<style lang="css" scoped>
.container {
  display: block;
}
.button {
  color: white;
  font-size: 2rem;
  transition: 0s all;
}

.button:hover {
  color: black;
  background-color: white;
}
</style>
