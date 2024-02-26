<template>
  <div class="element" :class="element.type">
    <h3 class="eNum">{{ element.number }}</h3>
    <h2 class="eSymbol">{{ element.symbol }}</h2>
  </div>
</template>

<script setup>
const props = defineProps(["element"]);
const element = props.element;
</script>

<style lang="css" scoped>

.eSymbol {
  font-size: 120%;
  margin-top: 0;
}
.element {
  height: 4.8vw;
  width: 4.8vw;
  background-color: #cbd5e0;
  border-collapse: collapse;
  color: black;
}
.dia-nonmetal {
  background-color: #faf089;
}
.noble {
  background-color: #fbd38d;
}
.alkali {
  background-color: #feb2b2;
}
.alkaline {
  background-color: #7f9cf5;
}
.metalloid {
  background-color: #90cdf4;
}
.poly-nonmetal {
  background-color: #81e6d9;
}
.tran-metal {
  background-color: #9ae6b4;
}
.post-tran-metal {
  background-color: #9ae6b4;
}
.lanthanide {
  background-color: #fbb6ce;
}
.actinide {
  background-color: #d6bcfa;
}
</style>
