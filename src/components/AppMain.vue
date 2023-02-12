<script >
import { store } from '../store';
import AppCard from './AppCard.vue';

export default{
  name:  'AppMain',
  data(){
    return{
      store
    };
  },
  components:{
    AppCard
  },
  methods:{
    
  },
};
</script>

<template>

  <main>
    <h2>
      Film
    </h2>
    <AppCard 
      v-for="movie in store.movies" 
      :element="movie"
      />
    
    <h2>
      Serie TV
    </h2>
    <AppCard 
      v-for="singleSeries in store.series" 
      :element="singleSeries"
      />
  </main>

</template>

<style scoped>

</style>
