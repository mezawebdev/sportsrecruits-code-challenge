<template>
  <div class="ReportTitle">
    <img src="/images/sr_insights_logo.png" />
    <h1>Academic Fit Report</h1>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/media";

.ReportTitle {
  margin-block-end: 2rem;

  @media (min-width: media.$md) {
    text-align: right;
  }

  img {
    width: 100%;
    max-width: 15.625rem;
  }

  h1 {
    font-size: 1.25rem;
    font-weight: normal;
  }
}
</style>
