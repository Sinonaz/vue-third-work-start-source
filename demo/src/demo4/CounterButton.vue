<script setup>
defineEmits(["action"]);
defineProps({
  disabled: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <button class="counter-button" @click="$emit('action')"  :disabled="disabled">
    <slot/>
  </button>
</template>

<style scoped lang="scss">
.counter-button {
  margin: 0 10px;
  font-size: 1.5rem;
  width: 2rem;
  height: 2rem;
  border-radius: 50%;
  border: none;
  background: #dd0000;
  color: white;
  cursor: pointer;

  &:hover,
  &:focus-visible{
    background: #ff0000;
  }

  &[disabled] {
    background: #999;
    cursor: not-allowed;
  }
}

</style>
