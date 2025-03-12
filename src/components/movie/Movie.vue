<script setup>
defineProps({
  Title: {type: String},
  Year: {type: String},
  imdbID: {type: String},
  Type: {type: String},
  Poster: {type: String}
})
</script>

<template>
  <div :id="imdbID" class="card movie">
    <div class="card-image waves-effect waves-block waves-light">
      <img v-if="Poster === 'N/A'" class="activator" :src="'https://via.placeholder.com/300x400?text='+Title"
           :alt="Title"/>
      <img v-else class="activator" :src="Poster" :alt="Title"/>
    </div>
    <div class='card-content'>
      <span class='card-title activator grey-text text-darken-4'>
          {{ Title }}
        </span>
      <p>
        {{ Year }}
      </p>
    </div>

  </div>
</template>