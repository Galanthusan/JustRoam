<template>
    <section id="navigation">
    <div class="nav">
        <select name="world">
            <option value="" disabled selected hidden>Сортировать по</option>
            <option value="country">Страна</option>
            <option value="town">Город</option>
        </select>
    </div>
    <img class="icon" src="../assets/images/icons/search.svg" alt="">
    </section>
</template>



<script>
    export default {
        name: 'HelloWorld',
        data () {
            return {
                msg: 'Welcome to Your Vue.js App'
            }
        }
    }
</script>
