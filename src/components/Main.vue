<template>
    <main>
        <input type="text" placeholder="cerca il film" v-model="userSearch">
        <button @click="getFilm" >cerca</button>
        <h2>FILM</h2>
        <div class="film-card">
            <FilmCard v-for="film  in apiFilmArray" :key="film.id" :details="film"/>
            <!-- <SeriesCard v-for="series  in apiSeriesArray" :key="series.id" :details="series"/>  -->
        </div>
        <h2>SERIE</h2>
        <div class="film-card">
            
            <FilmCard v-for="series  in apiSeriesArray" :key="series.id" :details="series"/> 
        </div>
    </main>
</template>
<script>
import axios from 'axios';

import FilmCard from "./FilmCard.vue"
// import SeriesCard from "./SeriesCard.vue"
export default {
  name: "Main",
  components: {
      FilmCard,
    //   SeriesCard,
    },
  data: function (){
      return {
          userSearch: '',
          apiFilmArray: [],
          apiSeriesArray: [],
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
             this.apiFilmArray = response.data.results;
            console.log(response.data.results)
        });
          axios.get('https://api.themoviedb.org/3/search/tv',{
            params: {
                api_key: '98fa6642cc307249e22192103cf1d9ae',
                query: this.userSearch,
            }
        })
        .then((responses) => {
             this.apiSeriesArray = responses.data.results;
            
        });
        
      },
      
    }
            
};
</script>


<style scoped lang="scss">
input{
    margin: 10px;
    border: 3px solid rgb(189, 177, 15);
    border-radius: 3px;
    padding:2px 5px ;
    color: rgba(230, 230, 230, 0.87);
}
button{
    border: 3px solid rgb(189, 177, 15);
    border-radius: 3px;
    padding: 2px 5px;
    font-size: 17px;
    color: rgba(230, 230, 230, 0.87);
}
.film-card{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    flex-grow: 1;
}
</style>