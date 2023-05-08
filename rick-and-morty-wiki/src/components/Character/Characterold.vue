<script setup>
import {ref} from 'vue'
import CharacterItem from './Character/CharacterItem.vue'

const props = defineProps(['id']);

const characterInfo = ref(null)
const getCharacterInfo = async () => {
  const response = await fetch(`https://rickandmortyapi.com/api/character/${props.id}`)
  .then(response => response.json())
  characterInfo.value = response
}

getCharacterInfo()
console.log(characterInfo)
</script>