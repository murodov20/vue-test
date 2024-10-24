<script setup>

import RecursiveFactorySetting from './components/RecursiveFactorySetting.vue';
import settings from './data.json';

</script>
<template>
  <div class="wrapper">
    <RecursiveFactorySetting :settings="settings" :depth="1" />
  </div>
</template>
<style>
.wrapper {
  display: flex;
  flex-direction: column;
}

.wrapper > * {
  text-align: left;
}
</style>