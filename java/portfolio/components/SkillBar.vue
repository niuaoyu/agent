<script setup lang="ts">
withDefaults(defineProps<{
  name: string
  value: number
  color?: string
}>(), {
  color: 'var(--accent)',
})
</script>

<template>
  <div class="skill-bar">
    <div class="skill-bar__meta">
      <span>{{ name }}</span>
      <span>{{ value }}%</span>
    </div>
    <div class="skill-bar__track">
      <div class="skill-bar__fill" :style="{ width: `${value}%`, background: color }" />
    </div>
  </div>
</template>
