<template>
    <section id="country-list">
        <div class="country" :class="country.class" v-for="country in countries">
            <div class="description">
                <img class="icon" :src="loadImage(country.url)" :alt="country.name">
                <h1>{{country.city}} {{country.name}}</h1>
                <p>{{country.description}}</p>
                <button class="get-more-btn" @click="openSidebar">Заказать тур</button>
                <div id="dot-icon" :class="country.class"> 
                    <div class="pulse-container">
                        <div class="pulse-box">
                            <div class="pulse-css"></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="slider">
                <carousel class="thailand" :autoplay="true" :perPage="1" :navigationEnabled="false" :paginationEnabled="false" >
                    <slide>
                        <img :src="loadSliderPicture(country.class,1)" alt="">
                    </slide>
                    <slide>
                        <img :src="loadSliderPicture(country.class,2)" alt="">
                    </slide>
                    <slide>
                        <img :src="loadSliderPicture(country.class,3)" alt="">
                    </slide>
                </carousel>
            </div>
        </div>
    </section>
</template>


<script>
    import countries from './data/countries.json'
    import { Carousel, Slide } from 'vue-carousel';
    import {EventBus} from './../bus.js';
    
    export default {
        components: {
            Carousel,
            Slide
        },
        name: 'CountryListComponent',
        data() {
            return {
               countries: countries
            }
        },
        methods: {
            loadImage (path) {
                console.log(path);
                return require('./../assets/images/icons/'+path)
            },
            loadSliderPicture (country, index) {
                //./../../src/assets/images/countries/content/'+country.class+'/2.jpg
                return require('./../assets/images/countries/content/'+country+'/'+index+'.jpg')
            },        openSidebar: function() {
                EventBus.$emit('show-tour-component');
            }
        }
    }
</script>
