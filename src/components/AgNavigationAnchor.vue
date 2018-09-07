<script lang="ts">

    import { Component, Prop, Vue } from "vue-property-decorator";

    @Component
    export default class AgNavigationAnchor extends Vue { }

</script>

<template>

    <div class="ag-navigation-anchor"></div>

</template>

<style lang="scss" scoped>

    @import "../style/_breakpoints";

    .ag-navigation-anchor {
        height: 64px;
        margin-top: -64px;

        @include for-desktop-up {
            height: 88px;;
            margin-top: -88px;
        }
    }

</style>