<script>
export default{
    name: 'AppCard',
    props: {
        element: Object
    },
    computed:{
        flag(){
            let lang = this.element.original_language;
            
            if(lang == 'en'){
                lang = 'uk';
            }
            else if(lang == 'pt'){
                lang = 'po';
            }

            const flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;

            return flag;
        },
        Cover(){
            const baseCoverUrl = 'https://image.tmdb.org/t/p/';
            const coverSize = 'w342';
            // const posterPath = this.element.poster_path;

            // console.log(baseCoverUrl, coverSize, posterPath);

            return baseCoverUrl + coverSize + this.element.poster_path;
        },  
    },
    methods: {
        getVote(){
            let newVote = this.element.vote_average;
            newVote = newVote / 2;
            newVote = Math.ceil(newVote);

            return newVote;
        }
    }
};
</script>

<template>
    <div>
        <img :src="Cover">
      <h3 v-if="element.title">
        {{ element.title }}
      </h3>
      <h3 v-else-if="element.name">
        {{ element.name }}
      </h3>
      <h4 v-if="element.original_title">
        {{ element.original_title }}
      </h4>
      <h4 v-else-if="element.original_name">
        {{ element.original_name }}
      </h4>
      <p>
        {{ element.original_language }}
      </p>
      <img :src="flag">
      <div>
        <span v-for="n in getVote()">
            ★
        </span>
        <span v-for="n in (5 - getVote())">
            ☆
        </span>
      </div>
    </div>
</template>

<style scoped>

</style>
