<template>
    <main>
        <input type="text" placeholder="cerca il film" v-model="userSearch">
        <button @click="getFilm">cerca</button>
        <div class="film-card">
            <FilmCard v-for="(film, index) in apiArray" :key="index" :details="film"/>
        </div>
    </main>
</template>
<script>
import axios from 'axios';

import FilmCard from "./FilmCard.vue"
export default {
  name: "Main",
  components: {
      FilmCard,
    },
  data: function (){
      return {
          userSearch: '',
          apiArray: [],
      }
  },
  methods: {
      getFilm: function(){
          axios.get('https://api.themoviedb.org/3/search/movie',{
            params: {
                api_key: '98fa6642cc307249e22192103cf1d9ae',
                query: this.userSearch,
            }
        })
        .then((response) => {
            this.apiArray = response.data.results;
            console.log(response.data.results)
        });
      }
    }
            
};
</script>


<style scoped lang="scss">
.film-card{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}
</style>