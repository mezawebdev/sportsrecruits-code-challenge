<template>
  <tr class="TableHeader">
    <th class="sticky">School Name</th>
    <th>Athletic Div</th>
    <th>Conference</th>
    <th>
      Ranking*<br /><span>(DI NCAA)<br />(DII & DIII Hero Sports)</span>
    </th>
    <th class="TableHeader__GPA">
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
</template>

<style scoped lang="scss">
.TableHeader {
  th {
    padding: 0.25rem 0.5rem;
    background: var(--dark-gray);
    color: white;
    font-weight: bold;

    span {
      font-weight: normal;
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
}
</style>
