<script setup>
import { ref, reactive } from "vue";
const counter = reactive({
  count: 0,
});
const num = ref(1);

const titleClass = ref("title");

function onIncreament() {
  num.value ? (counter.count += num.value) : counter.count++;
}
function onDescreament() {
  num.value ? (counter.count -= num.value) : counter.count--;
}
</script>

<template>
  <div class="counter-app">
    <div class="input">
      <button @click="onDescreament">descrease</button>
      <input v-model="num" type="number" />
      <button @click="onIncreament">increase</button>
    </div>
    <h2 :class="titleClass">{{ counter.count }}</h2>
    <button @click="counter.count = 0">reset</button>
  </div>
</template>

<style scoped>
.counter-app {
  overflow: hidden;
  border-top-left-radius: 0.6rem;
  border-top-right-radius: 0.6rem;

  box-shadow: hsl(160deg 100% 37%) 1px 7px 30px 0px;
}
.input {
  display: flex;
  justify-content: space-between;
}
.input input {
  width: 40px;
  text-align: center;
  flex: 1;
  padding: 1rem;
  border: none;
}

.input button {
  background-color: var(--primary-color);
  color: var(--color-text);
  border: none;
  cursor: pointer;
  padding: 1rem;
}
.title {
  padding: 1rem;
  text-align: center;
  background-color: aliceblue;
  color: var(--primary-color);
}
</style>
