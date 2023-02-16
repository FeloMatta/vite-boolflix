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
    <div class="element-card">
      <div class="front">
        <img :src="Cover">
      </div>
      <div class="back">
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

        <img :src="flag">
        <div>
          <span v-for="n in getVote()">
            <font-awesome-icon icon="fa-solid fa-star" />
          </span>
          <span v-for="n in (5 - getVote())">
            <font-awesome-icon icon="fa-regular fa-star" />
          </span>
        </div>
        <p>
          {{ element.overview }}
        </p>
      </div>
    </div>
</template>

<style lang="scss" scoped>
.element-card{
  position: relative;
  .front, .back{   
    width: 100%;
    height: 100%;
  }
  .front{
    img{
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  
  .back{
    display: none;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, .6);
    color: white;
    overflow-x: hidden;
    overflow-y: auto;
    padding: 15px;

    img{
      height: 40px;
      width: auto;
    }
  }

  &:hover{
    // .front{
    //   display: none;
    // }
    .back{
      display: block;
    }
  }
}

</style>
