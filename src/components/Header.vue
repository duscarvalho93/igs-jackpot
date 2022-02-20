<template>
    <div class="header">
        <Buttons />
        <Jackpot :jackpot="jackpot" />
        <Balance />
    </div>
</template>

<script setup>
    import Buttons from './header/Buttons.vue'
    import Jackpot from './header/Jackpot.vue'
    import Balance from './header/Balance.vue'
</script>

<script>
export default {
    props: {
        jackpot: {
            required: true
        }
    },

}
</script>


<style scoped>
    .header {
        width: 100%;
        min-height:180px;
        background-image: url('/src/assets/images/header.png');
        background-size: 100% 140px;
        background-repeat: no-repeat;
        background-position: top center;
        display: flex;
        place-items: flex-start;
        justify-content: space-between;         
    }

</style>