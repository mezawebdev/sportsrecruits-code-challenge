<script setup lang="ts">
defineProps<{
  name?: string;
  sport?: string;
  high_school?: { name: string };
  grad_year?: string;
  gpa?: number;
  club?: { name: string };
  major?: string;
  profile_image?: string;
}>();
</script>

<template>
  <div class="GeneralInfo">
    <div class="GeneralInfo__ProfilePicture">
      <div
        v-if="profile_image"
        :style="{ backgroundImage: `url(${profile_image})` }"
      ></div>
      <div v-else>orih32irh3</div>
    </div>
    <div class="GeneralInfo__Details">
      <h2>{{ name }}</h2>
      <div class="GeneralInfo__ExtraDetails">
        <div>
          <p><strong>Sport:</strong> {{ sport }}</p>
          <p><strong>Class:</strong> {{ grad_year }}</p>
          <p><strong>Club:</strong> {{ club ? club.name : "" }}</p>
        </div>
        <div>
          <p>
            <strong>High School:</strong>
            {{ high_school ? high_school.name : "" }}
          </p>
          <p><strong>GPA:</strong> {{ gpa }}</p>
          <p><strong>Desired Major:</strong> {{ major }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/media";

.GeneralInfo {
  @media (min-width: media.$md) {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  &__ProfilePicture {
    width: clamp(3.125rem, 1.319rem + 7.7vw, 6.25rem);
    height: clamp(3.125rem, 1.319rem + 7.7vw, 6.25rem);
    border-radius: 100%;
    flex-shrink: 0;

    @media (max-width: media.$md) {
      margin-block-end: 0.5rem;
    }

    div {
      width: 100%;
      height: 100%;
      border-radius: 100%;
      background-size: cover;
    }
  }

  &__Details {
    p + p {
      margin-block-start: 0.5rem;
    }

    h2 {
      color: var(--aqua);
      margin-block-end: 0.5rem;
    }
  }

  &__ExtraDetails {
    display: flex;
    gap: 5rem;
  }
}
</style>
