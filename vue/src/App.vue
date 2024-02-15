<script setup>
import { pTable as table } from './assets/table.js'
import Table from './components/Table.vue';
</script>

<template>
  <Table :class='table' :table="table"/>
</template>

<style scoped>
.table {
  margin: 0 0 0 0;
}
</style>
