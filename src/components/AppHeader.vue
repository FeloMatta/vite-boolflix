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
        <div class="logo-container">
            <h1>
                Boolfix
            </h1>
        </div>

        <div>
            <form action="" @submit.prevent="$emit('performSearch')">
                <input type="text" v-model="store.searchText" placeholder="Inserisci il nome di un film...">
                <button>
                    Search
                </button>
            </form>
        </div>
    </header>

</template>

<style lang="scss" scoped>
header{
    padding: 15px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;

    .logo-container{
        color: red;

        h1{
            text-transform: uppercase;
        }
    }
}
</style>
