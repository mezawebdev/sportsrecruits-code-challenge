<script setup lang="ts">
import TableGAPColorCell from "@/components/atoms/TableGPAColorCell.vue";
import type { Report } from "@/interfaces";
defineProps<{ report: Report; athleteGPA: number }>();
</script>

<template>
  <tr class="DataRow">
    <td class="DataRow__School sticky">{{ report.school }}</td>
    <td class="center">{{ report.division }}</td>
    <td>{{ report.conference }}</td>
    <td class="center">{{ report.ranking }}</td>
    <td class="DataRow__GPACell">
      <div>
        <span>{{ report.gpa.min }}</span>
        <span>{{ report.gpa["25%"] }}</span>
        <TableGAPColorCell
          :schoolAverage="report.gpa['50%']"
          :athleteGPA="athleteGPA"
        />
        <span>{{ report.gpa["75%"] }}</span>
        <span>{{ report.gpa.max }}</span>
      </div>
    </td>
    <td class="center">
      {{
        typeof report.sat.reading.min === "number" &&
        typeof report.sat.reading.max === "number"
          ? `${report.sat.reading.min}-${report.sat.reading.max}`
          : "Not Reported"
      }}
    </td>
    <td class="center">
      {{
        typeof report.sat.math.min === "number" &&
        typeof report.sat.math.max === "number"
          ? `${report.sat.math.min}-${report.sat.math.max}`
          : "Not Reported"
      }}
    </td>
    <td class="center">
      {{
        typeof report.act.min === "number" && typeof report.act.max === "number"
          ? `${report.act.min}-${report.act.max}`
          : "Not Reported"
      }}
    </td>
  </tr>
</template>

<style scoped lang="scss">
.DataRow {
  td {
    color: var(--dark-gray);
    padding: 0.35rem 0.5rem;
  }

  &:nth-child(odd):not(:first-child) {
    td {
      background: var(--light-gray);
    }
  }

  &:nth-child(even) {
    td {
      background: white;
    }
  }

  &__GPACell {
    position: relative;

    div {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      text-align: center;
      position: relative;
      height: 100%;
      position: absolute;
      width: calc(100% - (0.5rem * 2));
      top: 0;
      align-items: center;
      left: 0.5rem;

      span {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }
  }
}
</style>
