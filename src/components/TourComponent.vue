<template>
    <section id="tour">
        <div class="choose-type" v-if="currentSection === 'choose-type'">
            <img class="icon" src="./../assets/images/icons/bag.svg" alt="">
            <button class="country-selected" @click="displayHashtagSearch()">Я знаю, что хочу</button>
            <button class="budget-selected" @click="displayBudgetSearch()">У меня определенный бюджет</button>
        </div>
        
        <div class="hashtag" v-if="currentSection === 'hashtag-select'">
            <div class="hashtag-btn">
            <button>#Море</button>
            <button>#Тропики</button>
            <button>#Пальмы</button>
            <button>#Архитектура</button>
            <button>#Река</button>
            <button>#Океан</button>
            <button>#Горы</button>
            <button>#Катакомбы</button>
            <button>#Холмы</button>
            <button>#Остров</button>
            </div>
            <button class="tour-check-btn" @click="displayCountrySearch()">Подтвердить</button>
        </div>

        <div class="tour-select" v-if="currentSection === 'tour-select-price'">
            <div class="budget-selected">
                <div class="budget">
                    <h1>Введите бюджет</h1>
                    <textarea></textarea>
                </div>
                <div class="people-select">
                    <h1>Количетсво человек</h1>
                    <select name="people">
                        <option value="" disabled selected hidden></option>
                        <option value="1">1</option>
                        <option value="2">2</option>
                        <option value="3">3</option>
                        <option value="4">4</option>
                        <option value="5">5</option>
                        <option value="6">6</option>
                        <option value="7">7</option>
                    </select>
                </div>
                <button class="tour-check-btn">Подтвердить</button>
            </div>
        </div>

        <div class="tour-select" v-if="currentSection === 'tour-select-country'">
            <div class="country-selected">

                <div class="budget">
                    <h1>Введите бюджет</h1>
                    <textarea></textarea>
                </div>
                <button class="tour-check-btn">Подтвердить</button>
                </div>
            
            </div>
        
    </section>
</template>


<script>
    import {EventBus} from './../bus.js';

    export default {
        name: 'HelloWorld',
        data() {
            return {
                isVisible : false,
                msg: 'Welcome to Your Vue.js App',
                currentSection: 'choose-type',
                filterData: {
                    country_types: [
                        {name: 'Австрия, Зальцбург'},
                        {name: 'Италия, Бергамо'},
                        {name: 'Новая-Зеландия, Окленд'},
                        {name: 'Таиланд, Бангкок'},
                        {name: 'Япония, Токио'}
                    ],
                    people_amount: [
                        {value: 1},
                        {value: 2},
                        {value: 3},
                        {value: 4},
                        {value: 5},
                        {value: 6},
                        {value: 7},
                    ]
                }
            }
        },
        created() {
            let that = this;
            EventBus.$on('show-tour-component', function () {
                that.toggleComponent();
            });
        },
        methods: {
            setCurrentSection(name) {
                this.currentSection = name;
            },

            displayCountrySearch() {
                this.setCurrentSection('tour-select-country');
            },

            displayBudgetSearch() {
                this.setCurrentSection('tour-select-price');
            },
            
            displayHashtagSearch() {
                this.setCurrentSection('hashtag-select');
            },
            
            toggleComponent: function() {
              if(this.isVisible) {
                  this.hideComponent();
              }
              else {
                  this.showComponent();
              }
            },
 
            hideComponent: function () {
                this.isVisible = false;
                // this.$productMainFrame = $('#card-view');
                // this.$productNavigation.velocity('transition.bounceLeftOut');
                $('#tour').fadeOut();
            },
            
            showComponent: function() {
                console.log('bounceOut');
                this.isVisible = true;
                // $('#tour').velocity('transition.slideRightIn');
                $('#tour').fadeIn();
            }
        }


    }

</script>