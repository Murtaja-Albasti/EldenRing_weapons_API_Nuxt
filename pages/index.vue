<template>
<div class=" flex flex-col justify-center items-center bg-gradient-to-br from-amber-900 to-black max-w-full h-full">
   
    <h1 class=" text-9xl text-yellow-400 font-extrabold my-11 nabla-ER " style="user-select: none;">Elden Ring Weapons</h1>
    <!-- seg. -->
    <div class="p-2">
            <div
                class=" w-32 h-10 mb-5 flex justify-center items-center animate__flash animate__animated text-cyan-400 border-2 rounded-lg border-cyan-200 shadow-[0_0_2px_#fff,inset_0_0_2px_#fff,0_0_5px_#08f,0_0_15px_#08f,0_0_30px_#08f]"
            >
             by Murtaja
            </div>
        </div>    <!-- weapon card from api  -->

    <div class="grid grid-cols-4 gap-4">
        <div v-for="weapon in weapons" :key="weapon.id" class="max-w-sm items-center flex flex-col border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">

            <img class="rounded-t-lg " :src="weapon.image" alt="" />
            <div class="p-5">
                <a href="#">
                    <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ weapon.name }}</h5>
                </a>
                <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{{weapon.description}}</p>
            </div>
        </div>
    </div>

</div>
</template>

<script setup>
import {
    ref
} from 'vue'
import 'animate.css';

const weapons = ref([])

try {
    const data = await $fetch('https://eldenring.fanapis.com/api/weapons?limit=52')
    weapons.value = data.data
    console.log(weapons.value)
} catch (error) {
    console.error('Error fetching weapons:', error)
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nabla:EDPT,EHLT@67,16&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Kalnia+Glaze:wght@100..700&display=swap');
@import 'animate.css';



.nabla-ER {
  font-family: "Nabla", system-ui;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
  font-variation-settings:
    "EDPT" 67,
    "EHLT" 16;
}

.kalnia-glaze-NAME {
  font-family: "Kalnia Glaze", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
  font-variation-settings:
    "wdth" 100;
}
</style>