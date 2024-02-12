<template>
  <main class="">
    <section id="periodic-table">
      <div v-for="element in elements" :key="element.number"><Element number="element.number"/></div>
    </section>
    <h1>{{ table }}</h1>
  </main>
</template>

<script setup>
import Element from './Element.vue';
const props = defineProps(['table'])
const table = props.table
const elements = table.elements
</script>

<style lang="css" scoped>
  .table {
    display: grid;
    grid-template-columns: repeat(18, auto) 1fr;
    gap: 0.1vw;
  }
</style>