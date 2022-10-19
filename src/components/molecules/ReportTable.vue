<script setup lang="ts">
import type { Report } from "@/interfaces";
import TableRow from "@/components/atoms/TableRow.vue";
import TableHeader from "@/components/atoms/TableHeader.vue";

defineProps<{ reports: Report[]; athleteGPA: number }>();
</script>

<template>
  <div class="ReportTable">
    <table>
      <TableHeader />
      <TableRow
        v-for="report in reports"
        :report="report"
        :athleteGPA="athleteGPA"
      />
    </table>
  </div>
</template>

<style lang="scss">
.ReportTable {
  width: 100%;
  overflow-x: scroll;
  font-size: 0.75rem;

  .sticky {
    position: sticky;
    left: 0;
    width: 12.5rem;
    z-index: 5;
  }

  .center {
    text-align: center;
  }

  table {
    border-collapse: collapse;
    width: 100%;
    min-width: 62rem;
  }
}
</style>
