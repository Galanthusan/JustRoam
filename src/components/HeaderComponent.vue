<template>
    <header id="header">
        <img src="./../assets/images/logo.svg" alt="">
        <button class="tour-select" @click="showTourComponent()">Заказать тур</button>
    </header>
</template>


<script>
    import {EventBus} from './../bus.js';
    
    export default {
        name: 'HeaderComponent',
        data() {
            return {
                msg: 'Welcome to Your Vue.js App'
            }
        },
        methods: {
            showTourComponent: function () {
                EventBus.$emit('show-tour-component');
            }
        }
    }
</script>
