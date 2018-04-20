<template>
    <section id="video-background">
        <div class="video-background">
            <iframe width="1920" height="1080" src="https://www.youtube.com/embed/SJNgDAx85aI?rel=0&amp;autoplay=1" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>

    <div class="content-container">
        <div class="content">
            <h1>Австрия.</h1>
            <p>Зальцбург — небольшой город на западе Австрии. Живет в Зальцбурге всего 150 000 человек, но это не
                помешало
                городу иметь отличную троллейбусную сеть и постоянно ее развивать!</p>
            <a href="#" class="content-btn"  @click="openSidebar()">Заказать тур</a>
        </div>
    </div>
    </section>
</template>



<script>
    import {EventBus} from './../bus.js';
    export default {
        name: 'VideoComponent',
        data () {
            return {
                msg: 'Welcome to Your Vue.js App'
            }
        },
        methods: {
            openSidebar: function() {
                EventBus.$emit('show-tour-component');
            }
        }
    }
</script>
