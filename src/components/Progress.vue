<script setup>
import {computed } from 'vue';

const { totalBiden, totalTrump } = defineProps(['totalBiden', 'totalTrump']);

const totalVotes = computed(() => totalBiden + totalTrump);
const porcentagemBiden = computed(() => (totalBiden / totalVotes.value) * 100);
const porcentagemTrump = computed(() => (totalTrump / totalVotes.value) * 100);
</script>

<template>
  <div class="progress">
    <div class="biden" :style="{ width: `${Math.round(porcentagemBiden)}%`, left: '0' }">{{ totalBiden }}</div>
    <div class="trump" :style="{ width: `${Math.round(porcentagemTrump)}%`, right: '0' }">{{ totalTrump }}</div>
  </div>
</template>


  
<style scoped>
.progress {
  width: 50%;
  height: 30px;
  margin: 0 auto;
  position: relative;
}

.biden,
.trump {
  height: 100%;
  position: absolute;
  top: 0;
  font-weight: bold;
  color: white;
  padding: 3px 10px;
  box-sizing: border-box; /* Adicionado para incluir padding na largura total */
}

.biden {
  background-color: #93CAED;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
}

.trump {
  background-color: #F47174;
  text-align: end;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
}
</style>
