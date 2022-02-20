<template>
  <Carousel :items-to-show="1.2" :wrap-around="true">
    <Slide v-for="(page, key) in paginatedGames" :key="key" class="carousel_slide">
      <div class="carousel_item">
        <div class="games">

          <div v-for="(game, keyGame) in page" :key="keyGame"  class="game"  :class="keyGame == 0 ? 'highlight' : ''">
            <div class="box" :style="`background-image: url('${game.image}');`" @click="updateJackpotPanel(game.jackpot)">
              <div class="jackpot-value">
                <span class="frutigerColor">$ {{ game.jackpot }}</span>
              </div>
            </div>
          </div>

        </div>
      </div>
    </Slide>

    <template #addons>
      <Navigation />
      <Pagination />
    </template>
  </Carousel>
</template>

<script>
import { defineComponent } from 'vue';
import { Carousel, Navigation, Slide, Pagination } from 'vue3-carousel';

import 'vue3-carousel/dist/carousel.css';

export default defineComponent({
  components: {
    Carousel,
    Slide,
    Navigation,
    Pagination
  },

  data: () => {
    return {
      games : [],
      paginatedGames : [],
    }
  },

  props: {
    gamesPerPage : {
      default: 7,
    }
  },

  methods: {

    getPaginatedGames(games){

      const results = [];

      while (games.length) {
          results.push(games.splice(0, this.gamesPerPage));
      }
      return results;      

    },

    async getGames() {

      const request = await fetch('/data/games.json');
      const games = await request.json();
      this.games = games;
      this.paginatedGames = this.getPaginatedGames(games);

    },

    updateJackpotPanel(value){
      this.$emit("updateJackpotPanel", value);
    }
  },

  created(){
    this.getGames();
  }

});
</script>

<style>

  .carousel {
    width: 100%;
  }

  .carousel_slide {
    height: 400px;
  }

  .carousel_slide .carousel_item {
    width: 100%;
    height: 100%;
    margin: 0 20px;
    opacity: 0.2;
    transition: 0.5s;
  }

  .carousel__slide--visible > .carousel_item {
    opacity: 1;
  }

  .carousel__next, .carousel__prev {
    background-color: transparent;
    margin-top: -30px;
    width: 50px;
    height: 70px;
  }

  .carousel__prev {
    content: url('/src/assets/images/arrow_left.png');
    margin-left: 50px;
  }

  .carousel__next {
    content: url('/src/assets/images/arrow_right.png');
    margin-right: 50px;
  }

  .carousel__pagination button {
    background-image: url('/src/assets/images/pagination_off.png');
    width: 44px;
    height: 44px;
    background-color: transparent;
  }

  .carousel__pagination button.carousel__pagination-button--active {
    background-image: url('/src/assets/images/pagination_on.png');
  }
  .games {
    height: 100%;
    display: grid;
    grid-gap: 25px;
    grid-auto-flow: column;
  }

  .game {
    border-radius: 10px;
    overflow: hidden;
    border: 3px solid #ffbd00;
  }

  .game .box {
    height: 100%;
    background-size: cover;
    background-position: center center;
    display: flex;
    justify-content: center;
    place-items: end;   
    cursor: pointer; 

  }

  .jackpot-value {
    background-image: url('/src/assets/images/barra_jackpot.png');
    place-items: center;
    width: 259px;
    height: 50px;
    display: flex;
    justify-content: center; 
    font-size: 25px;  
    cursor: pointer;
  }

  .highlight {
    grid-area: 1 / 1 / span 2 / span 1;
  }
</style>