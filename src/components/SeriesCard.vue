<template>
    <div class="container">
        <h2>SERIE TV</h2>
        <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w342`+details.poster_path" alt="non c'è poster">
        </div>
        <div class="info">
            <ul>
                <li>Sommario:{{ details.overview }}</li>
                <li>Titolo:{{ details.name }}</li>
                <li>Titolo originale:{{ details.original_name }}</li>
                <li>
                    <div><img class="flag" :src="require(`../assets/img/${details.original_language}.png`)" :alt="details.original_language" ></div>
                </li>
                <li>Voto: <span v-html="star"></span> </li>
            
            
            </ul>
        
        </div>
    </div>
</template>

<script>
export default {
    name: "SeriesCard",
    props: {
        details: Object
    },
    data: function(){
        return{
           star: this.details.vote_average/2 ,
        //    image: this.details.original_language
        }
        
    },

    methods: {
        starConverter: function(){
            if(this.star === 0){
                this.star = `<span><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
            }else if(0 < this.star && this.star<= 1){
                this.star = `<span><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
            }else if(1 < this.star && this.star<= 2){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
            }else if (2<this.star && this.star<=3){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
            }else if (3<this.star && this.star<=4){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i></span>`
            }else if (4<this.star && this.star<=5){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></span>`
            }
            return this.star
        }

    },
    created: function() {
        this.starConverter()
    }
    
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
    :hover +.poster{
        display: none;
            
    }
    :hover +.info{
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