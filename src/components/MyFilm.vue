<template>
  
        <li class="single-card" >
                <img :src=" 'https://image.tmdb.org/t/p/w185' + item.poster_path" :alt=" 'cover for' + (item.title?item.title:item.name)">
                {{ item.title?item.title:item.name}} - 
                {{ item.original_title?item.original_title:item.original_name}} - 
                <img class="flag" v-if="availableFlags.includes(item.original_language)" :src=" require('../assets/' + item.original_language + '.png')"/> 
                <span v-else> {{ item.original_language }}</span>
                

                <div>
                    <i v-for="n in 5" class="fa-star" :class="(n>getVote(item.vote_average))?'fa-regular':'fa-solid'" :key="n">

                    </i>
                </div>
        </li>
  
</template>

<script>
export default {
name: 'MyFilm',
props:{
    item: Object
},
    data(){
        return {
        availableFlags: ['it', 'en']
        }
    },
    methods:{
        getVote(decimalVote){
            return Math.ceil(decimalVote / 2);
        }
    }
}
</script>

<style>

</style>