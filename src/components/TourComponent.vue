<template>
    <section id="tour">
        <div class="choose-type" v-if="currentSection === 'choose-type'">
            <img class="icon" src="./../assets/images/icons/bag.svg" alt="">
            <button class="country-selected" @click="displayHashtagSearch()">Я знаю, что хочу</button>
            <button class="budget-selected" @click="displayBudgetSearch()">У меня определенный бюджет</button>
        </div>

        <div class="hashtag" v-if="currentSection === 'hashtag-select'">
            <div class="hashtag-btn">
                <button v-for="hashtag in hashtags" :class="{checked: hashtag.checked}"
                        @click="hashtag.checked = !hashtag.checked">{{hashtag.name}}
                </button>
            </div>
            <button class="tour-check-btn" @click="displayCountrySearch()">Подтвердить</button>
        </div>

        <div class="tour-select" v-if="currentSection === 'tour-select-price'">
            <div class="budget-selected">
                <div class="budget">
                    <h1>Введите бюджет в день ($)</h1>
                    <input type="number" v-model="chosenPrice">
                </div>

                <button class="tour-check-btn" @click="displayCountrySearch()">Подтвердить</button>
            </div>
        </div>

        <div class="tour-select" v-if="currentSection === 'tour-select-country'">
            <div class="country-selected">
                <div class="checked-country" v-for="country in filteredCountries">
                    <h1 @click="displayQuestionForm">{{country.name}}, {{country.city}} — {{country.price_low}}$ -
                        {{country.price_high}}$ в
                        день</h1>
                </div>
                <button class="tour-check-btn" @click="displayChooseType">Я передумал</button>
            </div>
        </div>

        <div class="question-form" v-if="currentSection === 'question-form'">
            <div class="form">
                <h1>Введите имя</h1>
                <input type="text">
                <h1>Введите номер телефона</h1>
                <input type="text">
                <h1>Введите почту</h1>
                <input type="text">
            </div>
            <button class="tour-check-btn" @click="displayContactMessage">Подтвердить</button>
        </div>
        
        <div class="contact-message" v-if="currentSection === 'contact-message'">
            <h1>Спасибо!<br> С Вами свяжутся в ближайшее время :)</h1>
            <button class="close-btn" @click="hideComponent">Ok</button>
        </div>

    </section>
</template>


<script>
    import {EventBus} from './../bus.js';
    import countries from './data/countries.json'

    export default {
        name: 'TourComponent',
        data() {
            return {
                countries: countries,
                isVisible: false,
                msg: 'Welcome to Your Vue.js App',
                currentSection: 'choose-type',
                chosenPrice: null,
                hashtags: [
                    {name: '#море', alias: 'sea', checked: false},
                    {name: '#тропики', alias: 'tropics', checked: false},
                    {name: '#пальмы', alias: 'palm', checked: false},
                    {name: '#архитектура', alias: 'architecture', checked: false},
                    {name: '#река', alias: 'river', checked: false},
                    {name: '#океан', alias: 'ocean', checked: false},
                    {name: '#горы', alias: 'mountains', checked: false},
                    {name: '#катакомбы', alias: 'catacombs', checked: false},
                    {name: '#холмы', alias: 'hills', checked: false},
                    {name: '#остров', alias: 'island', checked: false},
                ]
            }
        },
        created() {
            let that = this;
            EventBus.$on('show-tour-component', function () {
                that.toggleComponent();
            });
        },
        computed: {
            /**
             * Return Boolean if we have any hashtags checked
             */
            isHashtagChecked: function () {
                return !!this.selectedHashTags.length;
            },
            /**
             * Return Array of hashtags that are selected
             */
            selectedHashTags: function () {
                return this.hashtags.filter(hashtag => {
                    return hashtag.checked;
                })
            },
            /**
             * Return filtered Countries by criteria
             * @returns {Array}
             */
            filteredCountries: function () {
                let component = this;
                return this.countries.filter(country => {
                    if (this.isHashtagChecked) {
                        // iF country contains one of selected hashtags
                        let sameTags = component.selectedHashTags.filter(function (n) {
                            console.log(n.alias);
                            return country.hashtags.indexOf(n.alias) !== -1;
                        });
                        if (sameTags.length) {
                            return true;
                        }
                    }
                    else {
                        if (component.chosenPrice) {
                            if (country.price_low <= component.chosenPrice && country.price_high >= component.chosenPrice) {
                                return true;
                            }
                        }
                    }

                });
            }
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
            displayChooseType() {
                this.chosenPrice = null;
                this.setCurrentSection('choose-type');
            },
            displayQuestionForm() {
                this.setCurrentSection('question-form')
            },

            displayContactMessage() {
                this.setCurrentSection('contact-message')
            },

            toggleComponent: function () {
                if (this.isVisible) {
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

            showComponent: function () {
                console.log('bounceOut');
                this.isVisible = true;
                // $('#tour').velocity('transition.slideRightIn');
                $('#tour').fadeIn();
            }
        }


    }

</script>