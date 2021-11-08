<template>
  <DefaultSlide>
    <template v-slot:title>Future of Front End Development</template>
    <template v-slot:content>
      <VideoWrapper class="intro-video" :v="v" :p="p" ref="video"></VideoWrapper>
      <a href="https://youtu.be/dNBLq6aLpCA?list=PLJNLwTPak6dhC5HGSud_mR1Lchhr8mXeT" class="slide__link">
        <b>Vue Mastery</b> Vue 3: The Future of Front End
      </a>
    </template>
  </DefaultSlide>
</template>

<script>
import DefaultSlide from '../DefaultSlide.vue'
import VideoWrapper from '../VideoWrapper.vue';
export default {
  name: "Future",
  components: {VideoWrapper, DefaultSlide},
  data: function(){
    return {
      p: 'Vue 3 The Future of Front End.png',
      v: 'Vue 3 The Future of Front End.webm',
    }
  },
}
</script>

<style scoped>
  .slide__link {
    text-decoration: none;
    color: var(--secondary-tint);
    margin: auto;
    font-size: 0.8em;
  }
  .slide__link:hover {
    text-decoration: underline;
  }
</style>
