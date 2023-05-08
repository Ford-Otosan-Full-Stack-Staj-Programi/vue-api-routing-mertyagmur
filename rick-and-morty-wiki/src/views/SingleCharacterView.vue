<script setup>
import { ref, onMounted } from 'vue'
import { getCharacterInfo } from "@/service/characters"
import {useRoute} from "vue-router";

const route = useRoute()

const characterInfo = ref(null)

onMounted(async () => {
  characterInfo.value = await getCharacterInfo(route.params.characterId)
})
</script>

<template>
    <div class="listing__item" v-if="characterInfo !== null">
        <img :src="characterInfo.image">
        <div class="listing__content">
            
            <h2>Character ID: {{ characterInfo.id }}</h2>
            <h2>Status: {{ characterInfo.status }}</h2>
            <h2>Species: {{ characterInfo.species }}</h2>
            <h2>Type: {{ characterInfo.type }}</h2>
            <h2>Origin: {{ characterInfo.origin.name }}</h2>
        </div>
      
    </div>
  </template>
  
  <style lang="scss" scoped>
  
  .listing {
    &__item {
      display: flex;
      flex-direction: row;
      align-items: flex-start;
      justify-content: flex-start;
  
      margin: 10px 0;
      padding: 20px;
  
      border-radius: 16px;
  
      background-color: lavender;
    }
    &__content{
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: flex-start;

      margin: 10px 0;
      padding: 10px;

      h2 {
        font-size: 32px;
      }
    }

  }
  </style>
  