<script setup lang="ts">
import GeneralInfo from "@/components/atoms/GeneralInfo.vue";
import ReportTitle from "@/components/atoms/ReportTitle.vue";
import ReportTable from "@/components/molecules/ReportTable.vue";
import type { Athlete } from "@/interfaces";

defineProps<{
  athlete: Athlete;
}>();
</script>

<template>
  <div class="AcademicFitReport">
    <div class="AcademicFitReport__Header">
      <ReportTitle />
      <GeneralInfo
        :name="athlete.name"
        :profile_image="athlete.profile_image"
        :sport="athlete.sport"
        :high_school="athlete.high_school"
        :grad_year="athlete.grad_year"
        :gpa="athlete.gpa"
        :club="athlete.club"
        :major="athlete.major"
      />
    </div>
    <ReportTable :reports="athlete.report" />
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/media";

.AcademicFitReport {
  border-top: 10px solid var(--aqua);
  border-bottom: 10px solid var(--aqua);
  padding-block: clamp(1.25rem, -0.638rem + 8.05vw, 5rem);
  padding-inline: 1rem;
  max-width: 90rem;
  margin-inline: auto;

  &__Header {
    margin-block-end: clamp(1.25rem, -0.638rem + 8.05vw, 5rem);

    @media (min-width: media.$md) {
      display: flex;
      flex-direction: row-reverse;
      gap: 1rem;
      justify-content: space-between;
    }
  }
}
</style>
