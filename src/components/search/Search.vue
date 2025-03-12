<script setup>
import {ref} from "vue";

const props = defineProps({
  searchMovies: {type: Function, default: ''},
})
const searchValue = ref("")
const type = ref('All')

function handleFilter(event) {
  type.value = event.dataset.type
  props.searchMovies(searchValue.value, type.value)
}
</script>

<template>
  <div class="row">
    <div class="input-field">
      <input
          class="validate"
          placeholder="Enter movie"
          v-model="searchValue"
          @keydown.enter="searchMovies(searchValue)"
      />
    </div>
    <div class="radio">
      <label for="all"  class="radio__label ">
        <input type="radio" id="all" value="All" v-model="type" />
        <span class="radio__text ">
          All
        </span>
      </label>
      <label for="movie" class="radio__label">
        <input type="radio" id="movie" value="Movie" v-model="type"/>
        <span class="radio__text">
          Movie
        </span>
      </label>
      <label for="series" class="radio__label">
        <input type="radio" id="series" value="Series" v-model="type"/>
        <span class="radio__text">
          Series
        </span>
      </label>
    </div>
  </div>
</template>

<style scoped>
.radio{
  display: flex;
  justify-content: space-between;
}
.radio__text{
  width:15rem;
}
span::after{
  background-color: #7e57c2 !important;
  border: none !important;
}
</style>