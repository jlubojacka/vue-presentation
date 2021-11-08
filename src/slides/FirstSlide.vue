<template>
    <div class="slide entry">
      <div class="bg"></div>
      <div class="bg bg2"></div>
      <div class="bg bg3"></div>
      <div class="content">
        <h1 class="entry__title"><VueLogo class="logo"></VueLogo>ue.js</h1>
        <h2 class="entry__subtitle">The Progressive Javascript Framework</h2>
        <p class="large">Jana Lubojacká</p>
      </div>
    </div>
</template>

<script>
import VueLogo from "../VueLogo.vue"
    export default {
        name: "FirstSlide",
      components: {VueLogo}
    }
</script>

<style scoped>
    .entry {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 5em 3em;
        font-size: 2.5vmin;
        position: relative;
    }
    .entry__title {
        border-radius: 0.5em;
        color: var(--secondary-tint);
        background-color: #d8d8d8;
        padding: 0.5em;
        width: 100%;
        text-align: center;
        letter-spacing: 2px;
    }
    .entry__subtitle {
        color: var(--secondary-tint);
    }
    .large {
        color: var(--secondary-tint);
        font-size: 1.3em;
        margin-bottom: 1em;
    }
    .bg {
      animation: slide 5s ease-in-out infinite alternate;
      background-image:
          linear-gradient(-60deg,
          var(--primary-tint) 50%,
          var(--secondary-tint) 50%);
      bottom: 0;
      left: -50%;
      opacity: 0.5;
      position: absolute;
      right: -50%;
      top: 0;
      z-index: 2;
    }
    .bg2 {
      animation-direction: alternate-reverse;
      animation-duration: 7s;
    }
    .bg3 {
      animation-duration: 6s;
    }

    @keyframes slide {
      0% {
        transform: translateX(-25%);
      }
      100% {
        transform: translateX(25%);
      }
    }

    .content {
      background-color: rgba(255,255,255,0.85);
      border-radius: 0.7em;
      box-shadow: 0 0 0.25em rgba(0,0,0,0.3);
      box-sizing: border-box;
      position: absolute;
      padding: 1em 2em;
      left: 50%;
      top: 50%;
      transform: translate(-50%,-50%);
      text-align: center;
      z-index: 3;
    }

    .logo {
      display: inline-block;
      width: 1.5em;
      height: 1.5em;
      transform: translate(0,0.2em);
      margin-right: -0.2em;
    }

</style>
