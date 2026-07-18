<script setup lang="ts">
defineProps<{
  index: string
  label: string
}>()
</script>

<template>
  <div class="section-label">
    <span>{{ index }}</span>
    <span class="section-label__line" />
    <span>{{ label }}</span>
  </div>
</template>
