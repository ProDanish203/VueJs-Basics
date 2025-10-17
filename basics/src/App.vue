<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <main class="min-h-screen w-screen bg-neutral-950 text-white overflow-x-clip">
    <div class="container mx-auto">
      <div class="flex items-center justify-center gap-x-8 w-full py-20">
        <a href="https://vite.dev" target="_blank" class="block">
          <img src="/vite.svg" class="size-10" alt="Vite logo" />
        </a>
        <a href="https://vuejs.org/" target="_blank" class="block">
          <img src="./assets/vue.svg" class="size-10" alt="Vue logo" />
        </a>
      </div>
      <HelloWorld title="Getting started with Vue.JS" />
    </div>
  </main>
</template>

<style scoped>
/* Scoped keyword will limit the styles to this component only */
</style>
