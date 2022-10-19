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
    <ReportTable :reports="athlete.report" :athleteGPA="athlete.gpa" />
    <div class="AcademicFitReport__Footer">
      <p>
        *Rankings for Division I schools based on NCAA data (www.ncaa.com) and
        rankings for Division II & III schools are based on data from Hero
        Sports (www.herosports.com/rankings)
      </p>
      <p>
        ** GPA is based on SportsRecruits members who have shown interest in
        (favorited) the school and have provided their GPA on their profile
      </p>
      <p>
        ***SAT and ACT scores based on national data provided by the National
        Center of Education Statistics- https://nces.ed.gov/ipeds/
      </p>
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/media";

.AcademicFitReport {
  border-top: 10px solid var(--aqua);
  border-bottom: 10px solid var(--aqua);
  padding-block: clamp(1.25rem, -0.638rem + 8.05vw, 5rem)
    clamp(1rem, 0.582rem + 1.78vw, 2.188rem);
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

  &__Footer {
    margin-block-start: clamp(3.125rem, 1.408rem + 7.32vw, 8rem);
    font-size: 0.85rem;

    p + p {
      margin-block-start: 0.5rem;
    }
  }
}
</style>
