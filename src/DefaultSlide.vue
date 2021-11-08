<template>
    <div class="slide">
        <h1 class="slide__title">
            <slot name="title">Slide title</slot>
        </h1>
        <h3 class="slide__subtitle" v-if="subtitle">{{subtitle}}</h3>
        <section class="slide__body">
            <slot name="content">

            </slot>
        </section>

    </div>
</template>

<script>
    export default {
        name: "DefaultSlide",
        props: {
            subtitle: {
                type: String
            }
        }
    }
</script>

<style scoped>

</style>
