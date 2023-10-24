<script setup lang="ts">
import { useField } from "vee-validate"
interface IProps {
  placeholder?: string
  name: string
}
const props = defineProps<IProps>()

const { value, errorMessage } = useField(() => props.name)
</script>

<template>
  <textarea :class="$style.textarea" :placeholder="props.placeholder" v-model="value"> </textarea>
  <span :class="$style.input__error" v-if="errorMessage">{{ errorMessage }}</span>
</template>
<style module lang="scss">
.textarea {
  appearance: none;
  min-height: 100px;
  padding-block: 10px;
  padding-inline: 15px;
  border: 1px solid #0505;
  font-size: 16px;
  font-family: Arial, sans-serif;
}

.textarea:active,
.textarea:focus,
.textarea:focus-visible {
  outline: 1px solid #000000;
}

.input__error {
  color: red;
  font-size: 12px;
  display: block;
}
.textarea::placeholder {
  font-family: Arial, sans-serif;
}
</style>
