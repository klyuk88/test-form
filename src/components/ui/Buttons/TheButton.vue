<script setup lang="ts">
interface IProps {
  title: string
}
const props = defineProps<IProps>()
const emit = defineEmits(["click"])
</script>

<template>
  <button @click="$emit('click')" :class="$style.btn">{{ props.title }}</button>
</template>
<style module lang="scss">
.btn {
  width: 100%;
  height: 55px;
  background: #000;
  color: #fff;
  border: none;
  transition: background-color 0.3s ease;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
}

.btn:hover {
  background: #444;
  transition: background-color 0.3s ease;
}
.btn:active {
  background: #666;
}

.btn:disabled {
  opacity: 20%;
  cursor: auto;
}
</style>
