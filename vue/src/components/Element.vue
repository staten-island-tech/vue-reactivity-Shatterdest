<template>
    <div>
        <h1>{{ number }}</h1>
    </div>
</template>

<script setup>
const props = defineProps(['number'])
const number = props.number

</script>

<style lang="css" scoped>

</style>