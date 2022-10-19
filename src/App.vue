<script setup lang="ts">
import AcademicFitReport from "@/components/templates/AcademicFitReport.vue";
import { data } from "./assets/data.json";
import type { Athlete } from "@/interfaces";

const athleteData = data[0] as Athlete;
</script>

<template>
  <main>
    <AcademicFitReport :athlete="athleteData" />
  </main>
</template>
