<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{
  name?: string;
  sport?: string;
  high_school?: { name: string };
  grad_year?: number;
  gpa?: number;
  club?: { name: string };
  major?: string;
  profile_image?: string;
}>();

function* chunks(arr: any[], n: number) {
  for (let i = 0; i < arr.length; i += n) {
    yield arr.slice(i, i + n);
  }
}

const athleteName = props.name ? props.name.split(" ") : null;
const alphabet = [...chunks("abcdefghijklmnopqrstuvwxyz".split(""), 6)];
const palette = [
  "#f1603c",
  "#6082fa",
  "#827cb8",
  "#0097a4",
  "#ffe066",
  "#ffa94d",
  "rgb(240, 240, 240)",
];
const paletteIndex = computed(() => {
  if (athleteName) {
    for (let i = 0; i < alphabet.length; i++) {
      if (
        alphabet[i].find((char) => {
          return char === athleteName[1].charAt(0).toLowerCase();
        })
      ) {
        return i;
      }
    }
  }

  return 6;
});
</script>

<template>
  <div class="GeneralInfo">
    <div class="GeneralInfo__ProfilePicture">
      <div
        v-if="profile_image"
        :style="{ backgroundImage: `url(${profile_image})` }"
      ></div>
      <div
        :style="{ backgroundColor: palette[paletteIndex] }"
        v-else
        class="GeneralInfo__ProfilePicturePlaceholder"
      >
        {{
          athleteName && athleteName.length > 0
            ? `${athleteName[0].charAt(0).toUpperCase()}${athleteName[1]
                .charAt(0)
                .toUpperCase()}`
            : ""
        }}
      </div>
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

  &__ProfilePicturePlaceholder {
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
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

    @media (max-width: media.$sm) {
      display: block;

      div + div {
        margin-block-start: 0.5rem;
      }
    }
  }
}
</style>
