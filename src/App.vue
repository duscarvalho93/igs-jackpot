<template>
  <Header :jackpot="jackpotValue" />
  <Content @updateJackpotPanel="updateJackpotPanel" />
  <Base />
</template>

<script>

import Header from './components/Header.vue'
import Base from './components/Base.vue'
import Content from './components/Content.vue'

export default {
  components: {
    Header,
    Content,
    Base
  },
  data() {
    return {
      jackpotValue: '0'
    }
  },
  methods: {
    updateJackpotPanel(value) {
      console.log(value)
      this.jackpotValue = value;
    }
  }
}
</script>


<style>
@import './assets/base.css';

  @font-face {
    font-family: 'Frutiger';
    src: url('/src/assets/fonts/FrutigerLTStd-Black.woff') format('woff');
    font-weight: normal;
  }


  #app {
    font-family: Frutiger;
    margin: 0 auto;
    font-weight: normal;
    width: 100%;
    display:flex;
    flex-direction: row;
    justify-content: space-between;
    place-items: center;
    height: 100vh;
    flex-flow: column;
  }

  .frutigerColor {
    background-image: linear-gradient(to bottom, #ffe773, #ffcb00, #ffad00);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    color: black;
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: #000;
  }


</style>