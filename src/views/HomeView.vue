<template>
  <MovieList @showMovieDetailEmit="showMovieDetail"></MovieList>
  <v-dialog v-model="visible">
    <MovieDetail @closeMovieDetailEmit="closeMovieDetail" v-if="visible===true" :movieId="selectedMovieId"></MovieDetail>
  </v-dialog>
</template>

<script>
import MovieDetail from '@/components/MovieDetail.vue';
import MovieList from '@/components/MovieList.vue';


export default {
    name: 'HomeView',
    components: { MovieList, MovieDetail },
    data(){
      return{
        visible : false,
        selectedMovieId : 0
      }
    },
    methods:{
      showMovieDetail(selectedMovieId){
        this.selectedMovieId = selectedMovieId;
        this.visible = true;
      },
      closeMovieDetail(){
        this.visible = false;
      }
    }
}

</script>
