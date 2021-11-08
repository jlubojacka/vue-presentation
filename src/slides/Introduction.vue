<template>
    <DefaultSlide>
        <template v-slot:title>Advantages</template>
        <template v-slot:content>
            <ul class="listing">
                <li>Easy to learn</li>
                <li>Flexibility</li>
                <li>Lightweight but still complex</li>
                <li>Good documentation</li>
                <li>Simple integration</li>
                <li>Customization</li>
                <li>... and many more!</li>
            </ul>
        </template>
    </DefaultSlide>
</template>

<script>
    import DefaultSlide from '../DefaultSlide.vue'

    export default {
        name: "Introduction",
        components: {DefaultSlide},

    }
</script>

<style scoped>

</style>
