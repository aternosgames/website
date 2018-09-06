<script lang="ts">

    import { Component, Prop, Vue } from "vue-property-decorator";

    @Component
    export default class AgContainer extends Vue {
        @Prop(Boolean) private fluid!: boolean;
    }

</script>

<template>

    <section :class="['ag-container', { fluid: fluid }]">
        <slot />
    </section>

</template>

<style lang="scss" scoped>

    @import "../style/_breakpoints";

    section.ag-container {
        margin: 0 auto;
        max-width: 1600px;
        padding: 12px;

        @include for-desktop-up {
            padding: 24px;
        }

        &.fluid {
            max-width: unset;
            width: 100%;
        }
    }

</style>
