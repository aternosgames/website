<template>

    <section :class="['container', { 'expand-v': expandVertically, fluid: fluid }]">
        <slot />
    </section>

</template>

<script lang="ts">

    import { Component, Prop, Vue } from 'vue-property-decorator';

    @Component
    export default class AgContainer extends Vue {
        
        @Prop({ type: Boolean, default: true }) private expandVertically!: boolean;
        @Prop(Boolean) private fluid!: boolean;
    
    }

</script>

<style lang="scss" scoped>

    @import "../style/_breakpoints";

    section.container {
        margin: 0 auto;
        max-width: 1600px;
        padding: 12px;

        @include for-desktop-up {
            padding: 24px;
        }

        &.expand-v {
            min-height: 100vh;
        }

        &.fluid {
            max-width: unset;
            width: 100%;
        }
    }

</style>