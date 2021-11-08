<template>
    <DefaultSlide subtitle="Concept Overview">
        <template v-slot:title>Model-View-ViewModel pattern</template>
        <template v-slot:content>
            <div class="cont">


              <figure class="cont__img">
                  <img :src="image" class="game-code slide__image" alt="MVVM diagram" width="1600" height="850">
              </figure>
              <p class="slide__text">every Vue instance is ViewModel</p>
            </div>
        </template>
    </DefaultSlide>
</template>

<script>
    import DefaultSlide from '../DefaultSlide.vue';
    export default {
        name: "MVVM",
        components: {DefaultSlide},
        data: function(){
            return {
                image: require('../assets/mvvm.png').default,
            }
        }
    }
</script>

<style scoped>
    .game-code {
        object-fit: contain;
        border: 1px solid rgba(195, 195, 195, 0.51);
    }
    .cont {
        display: grid;
        grid-template-rows: 88% 12%;
        max-height: 100%;
        margin:auto;
    }
    .cont__img {
        margin: 0 auto;
        width: 100%;
        height: auto;
    }
</style>
