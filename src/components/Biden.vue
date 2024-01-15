<script setup>
import {computed} from 'vue'
defineProps(['biden', 'totalBiden']);

</script>

<template>
  <div class="resultb">
    <table>
      <thead>
        <tr>
          <th>States</th>
          <th>Electoral Votes</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="state in biden" :key="state.state">
          <td>{{ state.state }}</td>
          <td>{{ state.electoralVotes }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.resultb {
  width: 100%;
  margin-top: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 0 20px;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: center;
}

th {
  background-color: #f2f2f2;
}

td{
  border-bottom: 1px solid #93CAED; /* Adiciona uma linha suave abaixo da célula */
}

</style>

