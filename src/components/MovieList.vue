<template>
    <v-container>
        <v-row justify="space-between">      
            <v-col v-for='result in movieFiltered' :key='result.id' cols="4">
                <v-card>
                    <v-card-title>{{ result.title }}</v-card-title>
                    <v-img :src="this.photopath + result.poster_path"
                    width="300"></v-img>
                    <v-btn @click=sendMovie(result.id) :width="500">PLUS D'INFOS</v-btn>
                </v-card>
            </v-col>
        </v-row>  
    </v-container>
</template>

<script>
import MovieDetail from './MovieDetail.vue';
import axios from 'axios';
import config from '../config.json';
import { computed, lodash } from 'vue'; //lodash ça marche pas de fou, tt pis lol

export default {
    name: 'MovieList',
    components: { MovieDetail },
    props:{
        recherche : String
    },
    data(){
        return{
            results : '',
            photopath : '',
            movieFiltered : []
        }
    },
    created(){
        axios.get(config.url.movie_list, {
            headers:{
                'Authorization' : `bearer ${config.api_key}`
            }
        })
        .then((res) =>{
            this.photopath = config.url.photo_path;
            this.results = res.data.results;
            this.movieFiltered = this.results;
            if(this.recherche !== ""){
                this.movieFiltered = lodash.filter(this.results,function(o){return  o.title.includes(this.recherche)});
            }
        })
    },
    methods:{
        sendMovie(selectMovieId){
            this.$emit('showMovieDetailEmit', selectMovieId);
        },
        closeMovieDetail(){
            
        }
    },

    
}
</script>