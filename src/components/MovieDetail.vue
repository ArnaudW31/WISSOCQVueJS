<template>
    <div>
        <!-- detail vue (v-dialog or something like this) -->
    </div>
</template>
<script>
export default {
    name: 'MovieDetail',
    props : {
        movieId : Number
    },
    created(){
        axios.get(config.url.movie_detail + this.movieId, {
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