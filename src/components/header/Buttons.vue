<template>
    <div class="buttons">
        <button class="btn btn-help"></button>
        <button class="btn btn-logout"></button>
    </div>

</template>

<style scoped>
    .buttons {
        margin-top: 5px;
        display: flex;
        width:33%;
    }

    .btn {
        background-color: transparent;
        border: none;        
        width: 87px;
        height: 88px;
        cursor: pointer;
    }
    .btn-help {
        background-image: url('/src/assets/images/help_idle.png');
    }
    .btn-logout {
        background-image: url('/src/assets/images/logout_idle.png');
    }
    .btn-help:active {
        background-image: url('/src/assets/images/help_pressed.png');
    }
    .btn-logout:active {
        background-image: url('/src/assets/images/logout_pressed.png');
    }

</style>
