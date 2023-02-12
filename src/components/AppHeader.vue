<script >
import { store } from '../store';

export default{
  name:  'AppHeader',
  data(){
    return{
        store
    };
  },
  components:{
    
  },
  methods:{

  }
}
</script>

<template>

    <header>
        <div>
            <input type="text" v-model="store.searchText" placeholder="Inserisci il nome di un film...">
            <button @click="$emit('performSearch')">
                Search
            </button>
        </div>
    </header>

</template>

<style scoped>

</style>
