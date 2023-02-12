<script>
import axios from 'axios';
import { store } from './store';

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default{
  name:  'App',
  data(){
    return{
      store
    };
  },
  components:{
    AppHeader,
    AppMain
  },
  methods:{
    handleSearchEvent(){

      this.makeSearch('movie');
      this.makeSearch('tv');
    },
    makeSearch(endpoint){
      let url= 'https://api.themoviedb.org/3/search/';
      console.log('searchText:', this.store.searchText);

      axios
        .get(url + endpoint, {
          params: {
            api_key: '7c95c89bad257022db0317c082c4edac',
            query: this.store.searchText,
            language: 'it-IT'
          }
        })
        .then((response)=> {
          console.log(response);

          if(endpoint == 'movie'){
          this.store.movies = response.data.results;
          }
          else{
          this.store.series = response.data.results;
          }
        });
    }
  },
};
</script>

<template>
  <AppHeader @performSearch="handleSearchEvent"/>
  <AppMain/>
</template>

<style>

</style>
