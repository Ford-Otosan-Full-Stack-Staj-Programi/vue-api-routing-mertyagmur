<script setup>
import { ref, onMounted } from 'vue'
import CharacterItem from './CharacterItem.vue'
import { getCharacters } from "@/service/characters"

const characters = ref([])

onMounted(async () => {
  characters.value = await getCharacters()
})

</script>

<template>
  <div  class="grid">
    <template v-for="character in characters">
        <div class="grid__item">
          <RouterLink :to="'/characters/' + character.id">
            <CharacterItem  :id="character.id"></CharacterItem>
          </RouterLink>
        </div>
      </template>
  </div>
</template>

<style lang="scss" scoped>
.grid {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-around;


  &__item {
    padding: 15px;
  }

}
</style>