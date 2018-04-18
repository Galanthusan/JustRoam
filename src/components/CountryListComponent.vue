<template>
    <section id="country-list">
        <div class="country" :class="country.class" v-for="country in countries">
            <div class="description">
                <img class="icon" :src="loadImage(country.url)" :alt="country.name">
                <h1>{{country.city}} {{country.name}}</h1>
                <p>{{country.description}}</p>
                <button class="get-more-btn">Заказать тур</button>
                <div id="dot-icon"> :class="country.class"
                    <div class="pulse-container">
                        <div class="pulse-box">
                            <div class="pulse-css"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>


<script>
    export default {
        name: 'HelloWorld',
        data() {
            return {
                countries: [
                    {
                        url:'thailand-compass.svg',
                        class: 'thailand',
                        name: 'Таиланд',
                        city: 'Бангкок,',
                        description: 'Здесь вам чудесный старый город с сотней буддийских храмов и современный деловой центр\n' +
                        '                с крутыми небоскребами.'
                    },
                    {
                        url:'italy-compass.svg',
                        icon: '../assets/images/icons/italy-compass.svg',
                        class: 'italy',
                        name: 'Италия',
                        city: 'Бергамо,',
                        description: 'Это один из многих совершенно удивительных, очаровательных, волшебных исторических городов Италии, в\n'+ 
                        'которые просто невозможно не влюбиться.'
                    },
                    {
                        url:'austria-compass.svg',
                        icon: '../assets/images/icons/italy-compass.svg',
                        class: 'austria',
                        name: 'Австрия',
                        city: 'Зальцбург,',
                        description: 'Живет в Зальцбурге всего 150 000 человек, но это не помешало городу иметь отличную троллейбусную\n'+
                        'сеть и постоянно ее развивать!'
                    },
                    {
                        url:'new-zealand-compass.svg',
                        icon: '../assets/images/icons/italy-compass.svg',
                        class: 'new-zealand',
                        name: 'Новая Зеландия',
                        description: 'В представлении людей Новая Зеландия — это страна с фантастической природой, красивыми бухтами,\n'+
                        'райскими пляжами и прекрасными удобными городами.'
                    },
                    {
                        url:'japan-compass.svg',
                        icon: '../assets/images/icons/italy-compass.svg',
                        class: 'japan',
                        name: 'Япония',
                        city: 'Токио,   ',
                        description: 'Говорят, японцы очень переживают, что не могут помочь и делают вид, что не слышат. Такое же\n'+
                        'поведение будет, если начать фотографировать японца без разрешения.'
                    },
                ]
            }
        },
        methods: {
            loadImage (path) {
                console.log(path);
                return require('./../assets/images/icons/'+path)
            },
        }
    }
</script>
