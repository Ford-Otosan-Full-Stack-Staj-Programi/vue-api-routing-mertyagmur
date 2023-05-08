<script setup>
import { ref, onMounted } from 'vue'
import { getCharacterInfo } from "@/service/characters"

const props = defineProps(['id']);
const characterInfo = ref(null)

onMounted(async () => {
  characterInfo.value = await getCharacterInfo(props.id)
})

</script>

<template>
  <div class="images" v-if="characterInfo !== null">
    <div class="images__item">
      <img :src="characterInfo.image">
      <h2>{{characterInfo.name}}</h2>
    </div>
  </div>
</template>

 <style lang="scss" scoped>


  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  


</style>