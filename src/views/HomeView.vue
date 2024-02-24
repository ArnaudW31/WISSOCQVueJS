<template>
  <MovieSearch @searchMovieEmit="setMovieSearch"></MovieSearch>

  <MovieList @showMovieDetailEmit="showMovieDetail" :recherche="this.recherche"></MovieList>

  <v-dialog v-model="visible">
    <MovieDetail @closeMovieDetailEmit="closeMovieDetail" v-if="visible===true" :movieId="selectedMovieId"></MovieDetail>
  </v-dialog>
</template>

<script>
import MovieDetail from '@/components/MovieDetail.vue';
import MovieList from '@/components/MovieList.vue';
import MovieSearch from '@/components/MovieSearch.vue';


export default {
    name: 'HomeView',
    components: { MovieList, MovieDetail, MovieSearch },
    data(){
      return{
        visible : false,
        selectedMovieId : 0,
        recherche : ""
      }
    },
    methods:{
      showMovieDetail(selectedMovieId){
        this.selectedMovieId = selectedMovieId;
        this.visible = true;
      },
      closeMovieDetail(){
        this.visible = false;
      },
      setMovieSearch(val){
        this.recherche = val;
      }
    }
}

</script>
