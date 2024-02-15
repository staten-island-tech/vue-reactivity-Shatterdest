<template>
  <main class="">
    <section id="periodic-table">
      <Element
        v-for="element in elements"
        :key="element.number"
        :element="element"
        :style="{ 'grid-column': element.xpos, 'grid-row': element.ypos }"
        @click="console.log(element)"
      />
    </section>
  </main>
</template>

<script setup>
import Element from "./Element.vue";
import ElementView from "../views/ElementView.vue"
const props = defineProps(["table"]);
const table = props.table;
const elements = table.elements;
</script>

<style lang="css" scoped>
#periodic-table {
  display: grid;
  grid-template-columns: repeat(18, auto) 1fr;
  gap: 0.1vw;
}
</style>
