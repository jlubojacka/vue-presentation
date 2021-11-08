<template>
    <DefaultSlide>
        <template v-slot:title>Thank you for your attention</template>
        <template v-slot:content>
          <div class="cont">
            <LogoAnimated class="vue-to-nuxt"></LogoAnimated>
            <p class="slide__text txt">Try out great framework <b>Nuxt.js</b></p>
            <iframe class="inline-website"
                    title="Nuxt.js website"
                    width="700"
                    height="500"
                    src="https://www.nuxtjs.org">
            </iframe>
          </div>

        </template>
    </DefaultSlide>
</template>

<script>
    import DefaultSlide from '../DefaultSlide.vue';
    import LogoAnimated from '../LogoAnimated.vue';
    export default {
        name: "LastSlide",
        components: {DefaultSlide, LogoAnimated},
        data: function(){
            return {

            }
        },
    }
</script>

<style scoped>
    .vue-to-nuxt {
      margin:auto;
      grid-area: logo;
    }

    .inline-website {
      width: 100%;
      height: 100%;
      margin:auto;
      grid-area: iframe;
    }

    .txt {
      grid-area: text;
    }

    .cont {
      display: grid;
      grid-template-columns: 35% 60%;
      grid-template-rows: auto 5em;
      grid-template-areas: "logo iframe" "text iframe";
      height: 100%;
      grid-column-gap: 5%;
    }

</style>
