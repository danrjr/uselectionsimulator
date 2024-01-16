<script setup>

import {reactive, computed} from 'vue'

import Result from './components/Result.vue'
import Progressbar from './components/Progressbar.vue'
import Biden from './components/Biden.vue'
import Trump from './components/Trump.vue'

const states = reactive([
  {state: 'Alabama', electoralVotes: 9, winner: 'T'},
  {state: 'Alaska', electoralVotes: 3, winner: 'T'},
  {state: 'Arizona', electoralVotes: 11, winner: ''},
  {state: 'Arkansas', electoralVotes: 6, winner: 'T'},
  {state: 'California', electoralVotes: 55, winner: 'B'},
  {state: 'Colorado', electoralVotes: 9, winner: 'B'},
  {state: 'Connecticut', electoralVotes: 7, winner: 'B'},
  {state: 'Delaware', electoralVotes: 3, winner: 'B'},
  {state: 'District of Columbia', electoralVotes: 3, winner: 'B'},
  {state: 'Florida', electoralVotes: 29, winner: 'T'},
  {state: 'Georgia', electoralVotes: 16, winner: ''},
  {state: 'Hawaii', electoralVotes: 4, winner: 'B'},
  {state: 'Idaho', electoralVotes: 4, winner: 'T'},
  {state: 'Illinois', electoralVotes: 20, winner: 'B'},
  {state: 'Indiana', electoralVotes: 11, winner: 'T'},
  {state: 'Iowa', electoralVotes: 6, winner: 'T'},
  {state: 'Kansas', electoralVotes: 6, winner: 'T'},
  {state: 'Kentucky', electoralVotes: 8, winner: 'T'},
  {state: 'Louisiana', electoralVotes: 8, winner: 'T'},
  {state: 'Maine', electoralVotes: 4, winner: 'B'},
  {state: 'Maryland', electoralVotes: 10, winner: 'B'},
  {state: 'Massachusetts', electoralVotes: 11, winner: 'B'},
  {state: 'Michigan', electoralVotes: 16, winner: ''},
  {state: 'Minnesota', electoralVotes: 10, winner: 'B'},
  {state: 'Mississippi', electoralVotes: 6, winner: 'B'},
  {state: 'Missouri', electoralVotes: 10, winner: 'T'},
  {state: 'Montana', electoralVotes: 3, winner: 'T'},
  {state: 'Nebraska', electoralVotes: 5, winner: 'T'},
  {state: 'Nevada', electoralVotes: 6, winner: 'B'},
  {state: 'New Hampshire', electoralVotes: 4, winner: 'B'},
  {state: 'New Jersey', electoralVotes: 14, winner: 'B'},
  {state: 'New Mexico', electoralVotes: 5, winner: 'B'},
  {state: 'New York', electoralVotes: 29, winner: 'B'},
  {state: 'North Carolina', electoralVotes: 15, winner: 'T'},
  {state: 'North Dakota', electoralVotes: 3, winner: 'T'},
  {state: 'Ohio', electoralVotes: 18, winner: 'T'},
  {state: 'Oklahoma', electoralVotes: 7, winner: 'T'},
  {state: 'Oregon', electoralVotes: 7, winner: 'B'},
  {state: 'Pennsylvania', electoralVotes: 20, winner: ''},
  {state: 'Rhode Island', electoralVotes: 4, winner: 'B'},
  {state: 'South Carolina', electoralVotes: 9, winner: 'T'},
  {state: 'South Dakota', electoralVotes: 3, winner: 'T'},
  {state: 'Tennessee', electoralVotes: 11, winner: 'T'},
  {state: 'Texas', electoralVotes: 38, winner: 'T'},
  {state: 'Utah', electoralVotes: 6, winner: 'T'},
  {state: 'Vermont', electoralVotes: 3, winner: 'B'},
  {state: 'Virginia', electoralVotes: 13, winner: 'B'},
  {state: 'Washington', electoralVotes: 12, winner: 'B'},
  {state: 'West Virginia', electoralVotes: 5, winner: 'T'},
  {state: 'Wisconsin', electoralVotes: 10, winner: ''},
  {state: 'Wyoming', electoralVotes: 3, winner: 'T'},
])

const bidenStates = reactive([])
bidenStates.push(...states.filter(s => s.winner == "B"))

const trumpStates = reactive([])
trumpStates.push(...states.filter(s => s.winner == "T"))

const swingStates = reactive([])
swingStates.push(...states.filter(s => s.winner == ''))

swingStates.forEach(s => {
  let numero = Math.random();
  if(numero <= 0.5){
    bidenStates.push(s)
  }
  else{
    trumpStates.push(s)
  }
})

const totalBiden = computed(() => {
  return bidenStates.reduce((acc, biden) => {
    return acc + biden.electoralVotes;
  }, 0);
});

const totalTrump = computed(() => {
  return trumpStates.reduce((acc, trump) => {
    return acc + trump.electoralVotes;
  }, 0);
});

</script>

<template>
  <div class="container">
    <Result :totalBiden="totalBiden" :totalTrump="totalTrump"/>
    <Progressbar :totalBiden="totalBiden" :totalTrump="totalTrump"/>
    <Biden :biden="bidenStates"/>
    <Trump :trump="trumpStates"/>
  </div>
</template>

<style scoped>
  .container{
    display: grid;
    width: 70%;
    margin: 0 auto;
    background-color: #dbdbdb;
    grid-template-columns: auto auto auto auto;
    grid-template-rows: auto auto auto; 
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
  }

  .container > :nth-child(1){
    grid-column: 1/-1;
    grid-row: 1
  }

  .container > :nth-child(2){
    grid-column: 1/-1;
    grid-row: 2;
  }

  .container > :nth-child(3){
    grid-column: 1/2;
    grid-row: 3;
  }

  .container > :nth-child(4){
    grid-column: 3/4;
    grid-row: 3;
  }
</style>

