<template>
    <div class="container">
        <div>
            <ul>
            <li>{{ details.title }}</li>
            <li>{{ details.original_title }}</li>
            <li>{{ details.original_language }}</li>
            <li>{{ details.vote_average }}</li>
            
        </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "FilCard",
    props: {
        details: Object
    }
}
</script>

<style scoped lang="scss">
.container{
    width: calc( (100% / 5) - 40px );
    margin: 20px;
    
    padding: 20px;
    text-align: left;
    ul{
        
        border: 2px solid white;
    }

}
</style>