<script setup>
import {onMounted, ref} from "vue";
import Movies from "@/components/movies/Movies.vue";
import Search from "@/components/search/Search.vue";

const API_KEY = "73cad48d"

const loading = ref(true)
const movies = ref([])

onMounted(()=>{
  fetch(`https://www.omdbapi.com/?apikey=${API_KEY}&s=matrix`)
      .then(res => res.json())
      .then(data => {
        movies.value = data.Search;
        loading.value = false
      })
      .catch((error)=>{
        console.log("Данные не обработались")
        loading.value = false
  })

})
function searchMovies(searchValue='matrix', type={}) {
  loading.value = true
  fetch(`https://www.omdbapi.com/?apikey=${API_KEY}&s=${searchValue}${type !== 'all' ? `&type=${type}` : ''}`)
      .then(response => response.json())
      .then(data => {
        movies.value = data.Search;
        loading.value = false
      })
}
</script>

<template>
  <main class="container content">
    <Search :searchMovies="searchMovies" />
    <div v-if="loading">Пустовато</div>
    <Movies v-else :movies="movies"/>
  </main>
</template>

<style scoped>
.content{
  min-height: calc(100vh - 70px - 64px);
  padding: 1.5rem;
}
</style>