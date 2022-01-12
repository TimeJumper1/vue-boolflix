<template>
    <div class="container">
        <div>
            <ul>
            <li>{{ details.name }}</li>
            <li>{{ details.original_name }}</li>
            <li>
                <div><img :src="require(`../assets/img/${details.original_language}.png`)" :alt= details.original_language ></div>
            </li>
            <li>{{ details.vote_average }}</li>
            
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
    data: function (){
        return{
            star: details.vote_average
        }

    },
    methods: {
        rateConverter: function(star){
            star = details.vote_average/2
        }
    },
}
</script>

<style scoped lang="scss">
.container{
    width: calc( (100% / 5) - 40px );
    margin: 20px;
    
    padding: 20px;
    text-align: left;
    ul{
        list-style-type: none;
        border: 2px solid white;
        img{
            width: 20px;
            height: auto;
            background-color: rgb(6, 11, 43);
        }
    }

}
</style>