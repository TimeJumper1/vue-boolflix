<template>
    <div class="container">
        <div>
            <ul>
                <li>
                    <div class="poster">
                        <img :src="`https://image.tmdb.org/t/p/w342`+details.poster_path" alt="">
                    </div>
                </li>
                <li>{{ details.name }}</li>
                <li>{{ details.original_name }}</li>
                <li>
                    <div><img class="flag" :src="require(`../assets/img/${details.original_language}.png`)" :alt= details.original_language ></div>
                </li>
                <li v-html="star">{{star}} </li>
            
            
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
            }else if(1 < this.star && this.star< 2){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
            }else if (2<this.star && this.star<3){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i><i class="far fa-star"></i></span>`
            }else if (3<this.star && this.star<4){
                this.star = `<span><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i></span>`
            }else if (4<this.star && this.star<5){
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
    
    margin: 20px;
    
    padding: 20px;
    text-align: left;
    ul{
        list-style-type: none;
        border: 2px solid white;
        .poster{
            width: 100%;
            height: auto;
        }
        .flag{
            width: 20px;
            height: auto;
            background-color: rgb(6, 11, 43);
        }
        
    }

}
</style>