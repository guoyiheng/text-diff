<script setup lang="ts">
import { isDark, toggleDark } from '~/composables'
</script>

<template>
  <nav flex items-center justify-center h-55px w-full bg-white dark:bg="#121212">
    <div icon-btn-primary i-file-icons:diff mr-1 scale-90 c-hex-9F353A />
    <h1 font-serif>Text <b text-primary>Diff</b></h1>
    <div w-auto flex-auto />
    <a icon-btn-primary i-carbon-logo-github rel="noreferrer" href="https://github.com/guoyiheng/text-diff"
      target="_blank" title="GitHub" mr-4 />
    <button icon-btn-primary @click="toggleDark()">
      <div v-if="isDark" i-carbon-moon />
      <div v-else i-carbon-sun />
    </button>
  </nav>
</template>
