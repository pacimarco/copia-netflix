<template>
  <div id="app">
   <MyHeader @search="searching"/>
   <MyMain :filmList="filmList" :seriesList="seriesList" />
   
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';

import axios from 'axios';

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain,
    
  },
  data(){
    return {
      apiUrl: 'https://api.themoviedb.org/3',
      apiKey: '92311e9e4318df2bfa2b9bcfe8d9adfe',
      language: 'it-IT',
      filmList : [],
      seriesList: [],

    }
  },
  methods:{
    searching(searchedText){

      const paramsObj = {
        params:{
          api_key: this.apiKey,
          language: this.language,
          query: searchedText,
        }
        
      };

      this.getMovies(paramsObj);
      this.getSeries(paramsObj);
    },

    getMovies(paramsObj){
      axios.get(this.apiUrl + '/search/movie', paramsObj)
      .then (res => {
        this.filmList = res.data.results;
      })
      .catch(err => {
        console.log(err);
      } );
    },

    getSeries(paramsObj){
      axios.get(this.apiUrl + '/search/tv', paramsObj)
      .then (res => {
        this.seriesList = res.data.results;
      })
      .catch(err => {
        console.log(err);
      } );
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';


</style>
