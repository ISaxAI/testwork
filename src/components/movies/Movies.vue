<script setup>
import Movie from "@/components/movie/Movie.vue";

const props = defineProps({
  movies: {type: Array, default: () => [], required: true},
})
</script>

<template>
  <div class="movies">
    <template v-if="movies.length">
      <Movie v-for="movie in props.movies" :key="movie.imdbID" v-bind="movie"/>
    </template>
  </div>
</template>

<style scoped>
.movies {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1rem;
}
</style>