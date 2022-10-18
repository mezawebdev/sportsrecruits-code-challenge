<script setup lang="ts">
import GeneralInfo from "@/components/GeneralInfo.vue";
import ReportTitle from "@/components/ReportTitle.vue";

defineProps<{
  athlete?: any;
}>();
</script>

<template>
  <div class="AcademicFitReport">
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
</template>

<style scoped lang="scss">
.AcademicFitReport {
  border-top: 10px solid var(--aqua);
  border-bottom: 10px solid var(--aqua);
  padding-block: 1.25rem;
  padding: 1rem;
  max-width: 64rem;
}
</style>
