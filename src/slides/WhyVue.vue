<template>
    <DefaultSlide>
        <template v-slot:title>Why Vue.js</template>
        <template v-slot:content>
          <VideoWrapper class="intro-video" :v="v" :p="p" ref="video"></VideoWrapper>
        </template>
    </DefaultSlide>
</template>

<script>
    import DefaultSlide from '../DefaultSlide.vue'
    import VideoWrapper from "../VideoWrapper.vue";

    export default {
      name: "WhyVue",
      components: {VideoWrapper,DefaultSlide},
      data: function(){
        return {
          p: 'Why choose Vue.js.png',
          v: 'Why choose Vue.js.webm',
        }
      },

    }
</script>

<style scoped>
  .intro-video {
    width: 85%;
    margin: auto;
  }
</style>
