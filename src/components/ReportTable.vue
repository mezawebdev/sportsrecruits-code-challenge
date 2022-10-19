<script setup lang="ts">
defineProps<{ reports: any[] }>();
</script>

<template>
  <div class="ReportTable">
    <table>
      <tr>
        <th>School Name</th>
        <th>Athletic Div</th>
        <th>Conference</th>
        <th>
          Ranking*<br /><span>(DI NCAA)<br />(DII & DIII Hero Sports)</span>
        </th>
        <th class="ReportTable__GPA">
          GPA**
          <div>
            <div>Min</div>
            <div>25%</div>
            <div>50%</div>
            <div>75%</div>
            <div>Max</div>
          </div>
        </th>
        <th>SAT Reading***<br />25%-75%</th>
        <th>SAT Math***<br />25%-75%</th>
        <th>ACT Composite***<br />25%-75%</th>
      </tr>
      <tr v-for="report in reports">
        <td>{{ report.school }}</td>
        <td class="center">{{ report.division }}</td>
        <td>{{ report.conference }}</td>
        <td class="center">{{ report.ranking }}</td>
        <td class="ReportTable__GPACell">
          <div>{{ report.gpa.min }}</div>
          <div>{{ report.gpa["25%"] }}</div>
          <div class="ReportTable__GPA50">{{ report.gpa["50%"] }}</div>
          <div>{{ report.gpa["75%"] }}</div>
          <div>{{ report.gpa.max }}</div>
        </td>
        <td class="center">
          {{
            report.sat.reading.min !== "N/A" && report.sat.reading.max !== "N/A"
              ? `${report.sat.reading.min}-${report.sat.reading.max}`
              : "Not Reported"
          }}
        </td>
        <td class="center">
          {{
            report.sat.math.min !== "N/A" && report.sat.math.max !== "N/A"
              ? `${report.sat.math.min}-${report.sat.math.max}`
              : "Not Reported"
          }}
        </td>
        <td class="center">
          {{
            report.act.min !== "N/A" && report.act.max !== "N/A"
              ? `${report.act.min}-${report.act.max}`
              : "Not Reported"
          }}
        </td>
      </tr>
    </table>
  </div>
</template>

<style scoped lang="scss">
.ReportTable {
  width: 100%;
  overflow-x: scroll;
  font-size: 0.75rem;

  .center {
    text-align: center;
  }

  table {
    border-collapse: collapse;
    width: 100%;

    tr:nth-child(odd) {
      background: var(--light-gray);
    }

    th,
    td {
      padding: 0.5rem;
      margin: 0;
    }

    th {
      background: black;
      color: white;
      font-weight: bold;

      span {
        font-weight: normal;
      }
    }

    table tr:nth-child(1) {
      background: black;
    }
  }

  &__GPA {
    div {
      display: flex;
      justify-content: space-evenly;
      margin-block-start: 0.25rem;

      * {
        width: 1.875rem;
        text-align: center;
      }
    }
  }

  &__GPACell {
    display: flex;
    justify-content: space-evenly;
    text-align: center;

    div {
      width: 1.875rem;
    }
  }

  &__GPA50 {
    background: red;
  }
}
</style>
