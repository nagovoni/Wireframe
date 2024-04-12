<template>
  <div class="text-center pa-4">
     <h1>Jokes</h1>
     <v-btn color="teal-darken-3" @click="addJoke">Add Joke</v-btn>
     <v-progress-linear v-if="isLoading" color="white" indeterminate></v-progress-linear>

      <v-card  v-for="(j, index) in store.jokes"
      :key="index"
      color="teal-darken-4"
      style="margin: 10px 0"
      >
        <v-list-item>{{ j.value }}
        </v-list-item>
        <v-list-item-avatar>
            <img :src="chuck" style="width: 110px; height: 80px;">
          </v-list-item-avatar>
      </v-card>

     <router-view></router-view>
  </div>
</template>

<script setup>

import axios from 'axios'
import { useJokesStore } from '@/store'
import {ref} from 'vue'
import chuck from '@/assets/chuck.png'

const isLoading = ref(false)


// access the `store` variable anywhere in the component ✨
const store = useJokesStore()

const addJoke = () => {
    isLoading.value = true
    axios.get('https://api.chucknorris.io/jokes/random').then ((res) =>{
    store.addJoke(res.data)
    isLoading.value = false
   }
  )
}

</script>
