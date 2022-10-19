<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{ athleteGPA: number; schoolAverage: number }>();
const gpaDiff = parseFloat((props.athleteGPA - props.schoolAverage).toFixed(2));
const color = computed(() => {
  if (gpaDiff === 0) return "#b4a7d6";
  if (gpaDiff >= 0.1 && gpaDiff > 0) return "#75ace5";
  if (gpaDiff < 0.1 && gpaDiff > 0) return "#a6a8da";
  if (gpaDiff >= -0.1 && gpaDiff < 0) return "#c194b5";
  if (gpaDiff < -0.1 && gpaDiff < 0) return "#d7737d";
  return "#222222";
});
</script>

<template>
  <span :style="{ backgroundColor: color }" class="DataRow__GPA50">{{
    schoolAverage
  }}</span>
</template>
