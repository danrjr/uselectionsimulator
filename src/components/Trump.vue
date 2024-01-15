<script setup>
defineProps(['trump', 'totalTrump']);
</script>

<template>
  <div class="resultt">
    <table>
      <thead>
        <tr>
          <th>States</th>
          <th>Electoral Votes</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="state in trump" :key="state.state">
          <td>{{ state.state }}</td>
          <td>{{ state.electoralVotes }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.resultt {
  width: 100%;
  margin-top: 20px;
}

table {
  width: 100%;
  margin-left: 65px;
  border-collapse: collapse;
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
  border-bottom: 1px solid #F47174; /* Adiciona uma linha suave abaixo da célula */
}
</style>

