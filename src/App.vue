<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <header>
    <h1 class="topic">Quizzler</h1>
  </header>

  <RouterView />
</template>

<style scoped>
.topic {
  color: #fff;
  font-size: 2rem;
  text-align: center;
  margin-top: 0;
  padding: 1rem;
}


</style>
