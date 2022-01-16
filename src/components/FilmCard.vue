<template>
    <div class="container">
        <div class="poster">
            <img v-if="details.poster_path" :src="`https://image.tmdb.org/t/p/w342`+details.poster_path" alt="">
             <img v-else src="../assets/img/assenza_poster.png" alt="non c'è poster">
        </div>
        <div class="info">
            <ul>
                <li v-if="details.overview">Sommario:{{ details.overview }}</li>
                <li v-else>Sommario: ci dispiace ma non ci sono sommari per questo elemento</li>
                <li v-if="details.title">Titolo:{{ details.title }}</li>
                <li v-else>Titolo:{{ details.name }}</li>
                <li v-if="details.original_title">Titolo originale:{{ details.original_title }}</li>
                <li v-else>Titolo originale:{{ details.original_name}}</li>
                <li v-if="flags.includes(details.original_language)">
                    <!-- aggiungere v-if per controllo  -->
                    <div><img class="flag" :src="require(`../assets/img/${details.original_language}.png`)" :alt="details.original_language"></div>
                </li>
                <li v-else>{{ details.original_language }}</li>
                <!-- <li>Voto: <span v-html="star"></span> </li> -->
                <li>Voto:<span v-for="voto  in 5" :key="voto"  >
                    <span v-if="star >= voto"><i class="fas fa-star"></i></span>
                    <span v-else><i class="far fa-star"></i></span>
                    </span>
                </li>
            
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "FilmCard",
    props: {
        details: Object
    },
    data: function(){
        return{
           star: parseInt(this.details.vote_average/2) ,
           flags: ['de', 'en' , 'es' , 'fr', 'gre' ,'it' ,'ja' , 'ko' , 'ru' , 'zh'],
          
        }
        
    },

    methods: {
        // trasformare il voto in stelle
        // starConverter: function(){
        //     if(this.star === 0){
        //         this.star = `<span><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
        //     }else if(0 < this.star && this.star<= 1){
        //         this.star = `<span><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
        //     }else if(1 < this.star && this.star<= 2){
        //         this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
        //     }else if (2<this.star && this.star<=3){
        //         this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
        //     }else if (3<this.star && this.star<=4){
        //         this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i></span>`
        //     }else if (4<this.star && this.star<=5){
        //         this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></span>`
        //     }
        //     return this.star
        // },
        

    },
    // inizializzare la funzione di conversione voto
    created: function() {
        // this.starConverter()
        
    },
    
}
</script>

<style scoped lang="scss">
.container{
    position: relative;
    margin: 20px;
    border: 2px solid rgba(230, 230, 230, 0.87);
    min-width: 343px;
    min-height: 513px;
    .poster{
       min-width: 343px;
        min-height: 513px; 
    }
    // elementi hover
    &:hover .poster{
        display: none;
            
    }
    &:hover .info{
        display: block;
    }
    .poster{
        width: 100%;
        height: auto;
        
        
    }
    .info{
        position: absolute;
        top: 0px;
        left: 0px;
        width: 100%;
        height: 100%;
        padding: 6px;
        display: none;
        ul{
        list-style-type: none;
            li{
                margin: 4px;
                .flag{
                width: 20px;
                height: auto;
                background-color: rgb(6, 11, 43);
                }
            }
        }
    }
    

}
</style>