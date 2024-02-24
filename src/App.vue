<template>
<div>
  <MovieList></MovieList>
</div>
</template>

<script>
import MovieList from './components/MovieList.vue';
import MovieDetail from './components/MovieDetail.vue'

export default {
    name: 'App',
    el: "#app",
    components: { MovieList }
}
</script>
<style>
.v-card{
  text-align: center;
}
.v-img{
  text-align: center;
}
</style>
