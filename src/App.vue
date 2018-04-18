<template>
    <div id="app">
        <header-component/>
        <tour-component/>
        <video-background-component/>
        <intro-component/>
        <navigation-component/>
        <country-list-component/>
        <instagram-photos-component/>
        <footer-component/>
    </div>
</template>


<script>
    import HeaderComponent from './components/HeaderComponent'
    import TourComponent from './components/TourComponent'
    import VideoBackgroundComponent from './components/VideoBackgroundComponent'
    import IntroComponent from './components/IntroComponent'
    import NavigationComponent from './components/NavigationComponent'
    import CountryListComponent from './components/CountryListComponent'
    import InstagramPhotosComponent from './components/InstagramPhotosComponent'
    import FooterComponent from './components/FooterComponent'


    export default {
        name: 'App',
        components: {
            HeaderComponent,
            TourComponent,
            VideoBackgroundComponent,
            IntroComponent,
            NavigationComponent,
            CountryListComponent,
            InstagramPhotosComponent,
            FooterComponent,


        }
    }
</script>
