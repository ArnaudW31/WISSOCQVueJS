<template>
    <v-container>
        <v-row justify="space-between">      
            <v-col v-for='result in results' :key='result.id' cols="4">
                <v-card>
                    <v-card-title>{{ result.title }}</v-card-title>
                    <v-img :src="this.photopath + result.poster_path"
                    width="300"></v-img>
                    <v-btn :width="500">PLUS D'INFOS</v-btn>
                </v-card>
            </v-col>
        </v-row>  
    </v-container>
    <MovieDetail v-if="selectMovieId !== null" :movieId="selectMovieId"></MovieDetail>
</template>

<script>

import axios from 'axios';
import config from '../config.json';
export default {
    name: 'MovieList',
    data(){
        return{
            results : '',
            photopath : '',
            selectMovieId : null
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
        })
    }
}

</script>