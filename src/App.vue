<script setup lang="ts">
import AcademicFitReport from "@/components/AcademicFitReport.vue";
import { data } from "./assets/data.json";
</script>

<template>
  <main>
    <AcademicFitReport :athlete="data[0]" />
  </main>
</template>

<style scoped>

</style>
