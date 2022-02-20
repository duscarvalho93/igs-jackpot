<template>
    <div class="balance">
        <span class="value frutigerColor">$
            <div v-if="showBalance" class="line"/>
            <span v-else> {{ balance }}</span>
        </span>
        <button @click="showBalance = !showBalance" class="btn" :class="showingBalance"></button> 
    </div>
</template>

<script>
export default {
    name: 'Balance',
    data() {
        return {
            balance: '23.000.00',
            showBalance: true,
        }
    },

    computed: {
        showingBalance() {
            return this.showBalance ? 'not-showing' : 'showing';
        }
    },  

}
</script>


<style scoped>
    .balance {
        width: 33%;
        place-items: center;
        font-size: 30px;
        padding-right: 4vw;
        margin-top: 26px;
        display: flex;
        justify-content: flex-end;
    }

    .btn {
        background-color: transparent;
        border: none;        
        width: 45px;
        height: 45px;
        margin-left: 10px;
        cursor: pointer;
        background-size: 100%;
    }
    .showing {
        background-image: url('/src/assets/images/eye_idle.png');
    }
    .showing:active {
        background-image: url('/src/assets/images/eye_pressed.png');
    }

    .not-showing {
        background-image: url('/src/assets/images/eye_off_idle.png');
    }
    .not-showing:active {
        background-image: url('/src/assets/images/eye_off_pressed.png');
    }

    .value {
        display: flex;
        place-items: center;
    }

    .line {
        width: 150px;
        height: 2px;
        background: linear-gradient(to bottom, #ffe773, #ffcb00, #ffad00);
        border: 2px solid black;
    }    

</style>