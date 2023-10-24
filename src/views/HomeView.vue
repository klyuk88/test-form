<script setup lang="ts">
import FormMainPage from "@/components/FormMainPage/FormMainPage.vue"
</script>

<template>
  <main>
    <div :class="$style.form_wrap"><FormMainPage /></div>
  </main>
</template>
<style module lang="scss">
.form_wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-block: 50px;
}
</style>
