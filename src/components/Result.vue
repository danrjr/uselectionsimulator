<script setup>
import {ref} from 'vue'
defineProps(['totalBiden', 'totalTrump'])

const trump = ref('https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Trump_Circle.png/599px-Trump_Circle.png')
const biden = ref('https://upload.wikimedia.org/wikipedia/commons/2/26/Biden_Circle.png')
</script>

<template>
    <div class="pai">
        <div class="bidenBanner">
            <img :src="biden" alt="" width="100px" height="100px" :class="{'preto_branco' : totalBiden < totalTrump}">
            <div>
                <h2>Biden</h2>
                <h3>Democratic</h3>
            </div>
        </div>

        <div class="bidenBanner">
            <div>
                <h2>Trump</h2>
                <h3>Republican</h3>
            </div>
            <img :src="trump" alt="" width="100px" height="100px" :class="{'preto_branco' : totalTrump < totalBiden}">
        </div>

    </div>
</template>

<style scoped>
    .pai{
        display: flex; 
        width: 100%; 
        justify-content: space-around;
    }

    .bidenBanner{
        display: flex;
        margin: 10px 50px;
    }

    h2{
        margin: 0 7px;
    }
    .preto_branco{
        filter: grayscale(100%);
    }
</style>