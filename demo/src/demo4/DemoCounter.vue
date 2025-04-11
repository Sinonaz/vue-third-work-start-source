<template>
  <demo-container>
    <div class="counter">

      <counter-button @action="counterStore.decrement" :disabled="counterStore.isDecrementDisabled">-</counter-button>

      <counter-value :value="counterStore.value"></counter-value>

      <counter-button @action="counterStore.increment">+</counter-button>

    </div>
  </demo-container>
</template>

<script setup>
import DemoContainer from "@/components/DemoContainer.vue";
import CounterButton from "@/demo4/CounterButton.vue";
import CounterValue from "@/demo4/CounterValue.vue";
import {useCounterStore} from "@/demo4/store";

const counterStore = useCounterStore();
</script>

<style lang="scss" scoped>
.counter {
  display: flex;
  align-items: center;
}
</style>
