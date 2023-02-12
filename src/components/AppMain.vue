<script >
import { store } from '../store';


export default{
  name:  'AppMain',
  data(){
    return{
      store
    };
  },
  components:{
    
  },
  methods:{
    getFlag(lang){
      if(lang == 'en'){
        lang = 'uk';
      }
      else if(lang == 'pt'){
        lang = 'po';
      }

      const flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;

      return flag;
    }
  },
};
</script>

<template>

  <main>
    <h2>
      Film
    </h2>
    <div v-for="movie in store.movies">
      <h3>
        {{ movie.title }}
      </h3>
      <h4>
        {{ movie.original_title }}
      </h4>
      <img :src="getFlag(movie.original_language)">
      <p>
        {{ movie.original_language }}
      </p>
      <p>
        {{ movie.vote_average }}
      </p>
    </div>
    <h2>
      Serie TV
    </h2>

    <div v-for="singleSeries in store.series">
      <h3>
        {{ singleSeries.name }}
      </h3>
      <h4>
        {{ singleSeries.original_name }}
      </h4>
      <img :src="getFlag(singleSeries.original_language)">
      <p>
        {{ singleSeries.original_language }}
      </p>
      <p>
        {{ singleSeries.vote_average }}
      </p>
    </div>
  </main>

</template>

<style scoped>

</style>
