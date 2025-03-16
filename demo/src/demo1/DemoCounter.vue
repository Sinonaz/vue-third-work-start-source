<template>
  <demo-container>
    <div class="counter">

      <counter-button @action="decrement">-</counter-button>

      <counter-value :value="count"></counter-value>

      <counter-button @action="increment">+</counter-button>

    </div>
  </demo-container>
</template>

<script setup>
import {ref} from "vue";
import DemoContainer from "@/components/DemoContainer.vue";
import CounterButton from "@/demo1/CounterButton.vue";
import CounterValue from "@/demo1/CounterValue.vue";

const count = ref(0)

/* Метод уменьшения значения */
const decrement = () => {
  if (count.value === 0) return;

  count.value = count.value - 1
}

/* Метод увеличения значения */
const increment = () => {
  count.value = count.value + 1
}
</script>

<style lang="scss" scoped>
.counter {
  display: flex;
  align-items: center;
}
</style>
