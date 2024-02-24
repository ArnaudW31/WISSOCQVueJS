<template>
    <div>
        <v-card :width="600">
            <v-card-title>
                {{ details.title }}
            </v-card-title>
            <v-img :src="this.photopath + details.poster_path"
                    height="300">
            </v-img>
            <v-chip v-for="genre in details.genres">
                {{ genre.name }}
            </v-chip>
            <v-rating v-model="details.vote_average" :length="10" readonly></v-rating>
            <v-divider></v-divider>
            <v-avatar v-for="producteur in details.production_companies" size="x-large">
                <v-img :src="this.photopath + producteur.logo_path">

                </v-img>
            </v-avatar>
            <v-divider></v-divider>
            <p>{{ details.overview }}</p>
            <v-divider></v-divider>
            <v-btn @click="closeDetail">
                FERMER
            </v-btn>
        </v-card>
    </div>
</template>
<script>
import axios from 'axios';

import config from '../config.json';

export default {
    name: 'MovieDetail',
    props : {
        movieId : Number
    },
    data(){
        return{
            details : '',
            photopath : ''
        }
    },
    created(){
        axios.get(config.url.movie_detail + this.movieId + "?language=fr-FR", {
            headers:{
                'Authorization' : `bearer ${config.api_key}`
            }
        })
        .then((res) =>{
            this.photopath = config.url.photo_path;
            this.details = res.data;
            console.log(res.data);
        })
    },
    methods:{
        closeDetail(){
            this.$emit('closeMovieDetailEmit');
        }
    }

}

</script>