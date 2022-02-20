<template>
    <div class="jackpot">
        <span class="frutigerColor title">JACKPOT</span><br>
        <span class="frutigerColor value">$ {{ jackpot }}</span>
    </div>
</template>


<script>
export default {
    props: {
        jackpot: {
            default: '0'
        }
    },

}
</script>

<style scoped>
    .jackpot {
        text-align: center;
    }

    .title {
        font-size:30px;
        font-weight: 800;
    }

    .value {
        font-size: 60px;
        font-weight: bolder;
    }
</style>