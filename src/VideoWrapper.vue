<template>
    <video class="slide__video" ref="video" @click="toggle" :controls="controls"
           :src="video" :poster="placeholder" preload="auto" loop muted/>
</template>

<script>
    export default {
        name: "VideoWrapper",
        props: {
            v: {type: String, required: true}, //video filename
            p: {type: String, required: true} //image placeholder filename
        },
        data: function(){
            return {
                debounceControls: null,
                controls: false, //show video control buttons (play/pause/sound...)
                video: require('./assets/' + this.v).default,
                placeholder: require('./assets/' + this.p).default
            }
        },
        methods: {
            toggle: function(){
                if (!this.controls){
                    let video = this.$refs.video;
                    if (video.paused || video.ended){
                        video.play();
                    } else {
                        video.pause();
                    }
                }

            },
            toggleControls: function(event){
                clearTimeout(this.debounceControls);
                this.debounceControls = setTimeout(() => {
                    if (event.code === "KeyC"){
                        event.preventDefault();
                        this.controls = !this.controls;
                    }
                }, 300);
            }
        },
        mounted() {
            window.addEventListener('keydown',this.toggleControls);
        },
        beforeDestroy(){
            window.removeEventListener('keydown',this.toggleControls);
            if (this.debounceControls){
                clearTimeout(this.debounceControls);
            }
        }
    }
</script>

<style>

</style>
