<script setup lang="ts">
defineProps<{
  number: string
  title: string
  description: string
  tags: string[]
  status?: string
}>()
</script>

<template>
  <article class="project-card">
    <div class="project-card__top">
      <span class="project-card__number">{{ number }}</span>
      <span v-if="status" class="project-card__status">{{ status }}</span>
    </div>
    <h3>{{ title }}</h3>
    <p>{{ description }}</p>
    <div class="tag-list">
      <span v-for="tag in tags" :key="tag" class="tag">{{ tag }}</span>
    </div>
  </article>
</template>
