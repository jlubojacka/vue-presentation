<template>
    <div id="app">
        <VSlides :slides="slides"></VSlides>
    </div>
</template>

<script>
    import VSlides from "./VSlides.vue";

    export default {
        name: "a1-App.vue",
        components: {
            VSlides
        },
        data: function(){
            return {
                //list of component names in slides directory
                slides: [
                    {comp: "FirstSlide"},
                    {comp: "Introduction"},
                    {comp: "WhyVue"},
                    {comp: "MVVM"},
                    {comp: "Future"},
                    {comp: "LastSlide"}
                ]
            }
        }
    }
</script>

<style scoped>
    #app {

    }

</style>
<style>
    /* open-sans-regular - latin-ext_latin */
    @font-face {
        font-family: 'Open Sans';
        font-style: normal;
        font-weight: 400;
        font-display: swap;
        src:
        url('./assets/fonts/open-sans-v18-latin-ext_latin-regular.woff2') format('woff2'), /* Chrome 26+, Opera 23+, Firefox 39+ */
        url('./assets/fonts/open-sans-v18-latin-ext_latin-regular.woff') format('woff'); /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
    }
    /* open-sans-italic - latin-ext_latin */
    @font-face {
        font-family: 'Open Sans';
        font-style: italic;
        font-weight: 400;
        font-display: swap;
        src:
        url('./assets/fonts/open-sans-v18-latin-ext_latin-italic.woff2') format('woff2'), /* Chrome 26+, Opera 23+, Firefox 39+ */
        url('./assets/fonts/open-sans-v18-latin-ext_latin-italic.woff') format('woff'); /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
    }
    /* open-sans-600 - latin-ext_latin */
    @font-face {
        font-family: 'Open Sans';
        font-style: normal;
        font-weight: 600;
        font-display: swap;
        src:
                url('./assets/fonts/open-sans-v18-latin-ext_latin-600.woff2') format('woff2'), /* Chrome 26+, Opera 23+, Firefox 39+ */
                url('./assets/fonts/open-sans-v18-latin-ext_latin-600.woff') format('woff'); /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
    }

    body {
        margin: 0;
    }
    :root {
        --primary-tint: #41b883;
        --secondary-tint: #2d3f56;
    }
    * {
        box-sizing: border-box;
        font-family: 'Open Sans';
        word-spacing: 1px;
    }
</style>
