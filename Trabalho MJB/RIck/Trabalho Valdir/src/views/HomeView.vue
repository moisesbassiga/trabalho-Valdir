<script setup>
import { onMounted, reactive, ref } from 'vue';
import ListCharacters from '../components/ListCharacters.vue';

let characters = reactive(ref());

onMounted(() => {
  fetch("https://rickandmortyapi.com/api/character")
.then(response => response.json())
.then(response => {
    characters.value = response.results
    console.log(characters)
  })
})
</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-12">
          <div class="card">
            <div class="card-body row">
              <ListCharacters 
                v-for="character in characters"
                :key="character.id"
                :character="character"
                />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style>

</style>