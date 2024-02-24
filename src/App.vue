<template>
<div>
  <HomeView></HomeView>
</div>
</template>

<script>
import HomeView from './views/HomeView.vue';

export default {
    name: 'App',
    el: "#app",
    components: { HomeView }
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
