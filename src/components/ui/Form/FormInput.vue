<script setup lang="ts">
import { useField } from "vee-validate"
import { vMaska } from "maska"
interface IProps {
  type: "text" | "tel" | "email"
  placeholder?: string
  name: string
  mask?: string
}

const props = withDefaults(defineProps<IProps>(), {
  type: "text"
})
const { value, errorMessage } = useField(() => props.name)
</script>
<template>
  <div :class="$style.input_wrap">
    <input
      :type="props.type"
      :placeholder="props.placeholder"
      :class="$style.input"
      v-model="value"
      v-maska
      :data-maska="props.mask ?? null"
    />
    <span :class="$style.input__error" v-if="errorMessage">{{ errorMessage }}</span>
  </div>
</template>

<style module lang="scss">
.input {
  display: block;
  height: 45px;
  padding-block: 10px;
  padding-inline: 15px;
  border: 1px solid #0505;
  font-size: 16px;
  width: 100%;
  box-sizing: border-box;
}
.input:active,
.input:focus,
.input:focus-visible {
  outline: 1px solid #000000;
}

.input__error {
  color: red;
  font-size: 12px;
  display: block;
}

.input_wrap {
  width: 100%;
}
</style>
