<template>
<table>
  <thead>
    <tr>
      <table-head v-for="column in columns"
                  :key="column"
                  :column="column"
                  :data="rowsByColumn[column]">
      </table-head>
    </tr>
  </thead>
  <tbody>
    <tr v-for="row in data">
      <td v-for="cell, column in row">
        {{ column }}:
        <slot :name="column" :value="cell">
          {{ cell }}
        </slot>
      </td>
    </tr>
  </tbody>
  <!-- Another Table-Component might have multiple tbody-Nodes -->
</table>
</template>

<script>
import TableHead from './TableHead.vue'

export default {
  props: ['columns', 'data', 'rowsByColumn'],
  components: {
    TableHead
  }
}
</script>

<style scoped>
table th, table td {
  border: 1px solid black;
}
</style>
