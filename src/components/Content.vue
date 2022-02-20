<template>
    <div class="container">
        <Carousel @updateJackpotPanel="updateJackpotPanel" />
    </div>
</template>

<script>

import Carousel from './Carousel.vue'
export default {
    components: {
        Carousel,
    },
    props: {
        jackpot: {
            default: '0'
        }
    },

    methods: {
        updateJackpotPanel(value){
        this.$emit("updateJackpotPanel", value);
        }
    }

}
</script>



<style scoped>
    .container {
        width: 100%;
        max-width: 1920;
    }
</style>