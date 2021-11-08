
<template>
    <div v-if="slides.length > 0" class="slides">
        <div class="slide-wrapper">
            <transition name="fadebin" mode="out-in">
              <keep-alive>
                <component v-bind:is="currSlideComp" :currSlide="currSlide"></component>
              </keep-alive>
            </transition>
            <div class="slide__footer">
                <span class="footer__item footer__text">Jana Lubojacká</span>
                <span class="footer__item footer__text">Vue.js presentation</span>

                <div class="footer__btns footer__item">
                    <button class="footer__btn footer__btn--back" @click="prevSlide"></button>
                    <span>{{currSlide + 1}}/{{slides.length}}</span>
                    <button class="footer__btn footer__btn--next" @click="nextSlide"></button>
                </div>
            </div>
        </div>
    </div>
</template>


<script>

    export default {
        name: "VSlides",
        components: {

        },
        props: {
            slides: {
                type: Array,
                default: () => {return []}
            }
        },
        provide: function(){
          return {
              slidesTotal: this.slides.length,
          }
        },
        data: function(){
            return {
                currSlide: 0,
            }
        },
        computed: {
            currSlideComp: function(){
                return this.slides.length > 0 ? this.slides[this.currSlide].comp : null;
            }
        },
        methods: {
            nextSlide: function(){
                let newIdx = Math.min(this.currSlide + 1, this.slides.length - 1);
                if (newIdx !== this.currSlide){
                    this.currSlide = newIdx;
                }
            },
            prevSlide: function(){
                let newIdx = Math.max(0, this.currSlide - 1);
                if (newIdx !== this.currSlide){
                    this.currSlide = newIdx;
                }
            },
            firstSlide: function(){
              this.currSlide = 0;
            },
            lastSlide: function(){
              this.currSlide = this.slides.length - 1;
            },
            handleKey: function(e){
                switch (e.code) {
                    case 'ArrowLeft':
                    case 'KeyA':
                        e.preventDefault();
                        this.prevSlide();
                        break;
                    case 'ArrowRight':
                    case 'KeyD':
                        e.preventDefault();
                        this.nextSlide();
                        break;
                    case 'Home':
                    case 'KeyW':
                        e.preventDefault();
                        this.firstSlide();
                        break;
                    case 'End':
                    case 'KeyS':
                        e.preventDefault();
                        this.lastSlide();
                        break;
                }
            }
        },
        created(){
          for (let slide of this.slides){
              this.$options.components[slide.comp] = require('./slides/' + slide.comp + ".vue").default
          }
        },
        mounted(){
            window.addEventListener('keydown', this.handleKey)
        },
        beforeDestroy() {
            window.removeEventListener('keydown',this.handleKey);
        }
    }

</script>


<style scoped>
    .slides {
        width: 100vw;
        height: 100vh;
        margin: auto;
        background-color: rgba(128, 128, 128, 0.3);
        overflow: hidden;
    }

    .fadein-enter-active, .fadein-leave-active {
        transition: opacity 0.2s ease-in-out;/*cubic-bezier(0.7, 0, 0.84, 0);*/

    }
    .fadein-enter, .fadein-leave-to {
        opacity: 0;
    }


    .slide__footer {
        height: var(--footer-height, 5%);
        width: 100%;
        display: flex;
        color: white;
        flex-grow:0;
        align-self: flex-end;
        align-items: stretch;
        background-color: var(--primary-tint);
        font-size: 0.6em;
    }
    .footer__item {
        flex-basis: 33.3%;
        text-align: center;
        margin: 0;
        height: 100%;
        /*padding: 0.35em;*/
    }
    .footer__text {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .footer__item:nth-child(2){
        background-color: var(--secondary-tint);
    }
    .footer__btns {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 0.6em;
    }
    .footer__btn {
        background-color: transparent;
        border: none;
        outline: none;
        color: white;
        font-size: 1em;
        font-weight: 500;
        cursor: pointer;
    }
    .footer__btn--back:after {
        content: "<"
    }
    .footer__btn--next:after {
        content: ">"
    }
    /*
    .slide-wrapper:after {
        padding-top: 75%;
    }
    */
    .slide-wrapper {
        margin: auto;
        display: flex;
        flex-direction: column;
        max-height: 100vh;
        background-color: #ffffff;
        box-shadow: 0 0px 1px rgba(0,0,0,0.09),
        0 0px 2px rgba(0,0,0,0.10),
        0 2px 4px rgba(0,0,0,0.11),
        0 4px 8px rgba(0,0,0,0.12);
        aspect-ratio: 4/3;
    }
    @supports not (aspect-ratio: 4/3){
        .slide-wrapper {
            position: relative;
            width: calc(100vh * (4/3));
            height: 100vh;
        }
        @media screen and (orientation: portrait){ /*width < height*/
            .slide-wrapper {
                width: 100vw;
                height: calc(100vh * (3/4));
            }
        }
    }


</style>

<style>
    body {
      font-size: 3.9vmin;
      --footer-height: 5%;
    }
    .slide {
        display: flex;
        flex-direction: column;
        height: calc(100% - var(--footer-height));
        width: 100%;
        overflow: hidden;
    }

    .slide__title {
        text-align: center;
        color: white;
        background-color: var(--primary-tint);
        padding: 0.45em 0.7em;
        margin: 0;
        font-weight: 500;
        font-size: 1.3em;
    }

    .slide__subtitle {
        margin: 0;
        text-align: center;
        color: white;
        background-color: var(--secondary-tint);
        padding: 0.5em 1em;
        font-size: 0.75em;
    }

    .slide__body {
        padding: 1.3em 2em;
        flex-grow: 1;
        display: flex; /*for centering*/
      flex-direction: column;
        font-weight: 500;
        height: 100%;
        max-height: 100%;
        overflow: hidden;
    }
    .slide__image,
    .slide__video {
        max-width: 100%;
        display: block;
        margin: auto;
    }
    .slide__image {
        max-height: 100%;
    }
    .slide__text {
        font-size: 0.9em;
        text-align: center;
    }
    p.slide__text {
      margin-top: 0;
    }
    .listing {
        line-height: 1.85;
        height: 100%;
        margin: 0;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
</style>
