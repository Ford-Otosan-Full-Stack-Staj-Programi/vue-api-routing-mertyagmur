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
  align-items: flex-start;
  justify-content: flex-start;


  &__item {
    width: calc(100% / 4);
    aspect-ratio: 4/3;

    padding: 10px;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

}
</style>