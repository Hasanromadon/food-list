<template>
  <div class=" w-full p-4 flex justify-center">
    <input type="text" class=" w-3/4 border-2 border-gray-300 rounded-sm" placeholder="Search foods..." />
  </div>
  <div class="flex gap-1 justify-center">
    <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters" :key="letter">
      {{ letter }}
    </router-link>
  </div>
</template>

<script setup>
import {onMounted, ref} from 'vue'
import axiosClient from '../axiosClient.js';

const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('')
const ingredients = ref([]) 
onMounted(async()=> {

  const response = await axiosClient.get('/list.php?i=list'); 
  ingredients.value = response.data;


})

</script>