<script lang="ts">

    import { Component, Vue } from "vue-property-decorator";

    import AgContainer from "@/components/AgContainer.vue";

    @Component({
        components: {
            AgContainer
        },
    })
    export default class Home extends Vue {}

</script>

<template>

    <ag-container expand-vertically="true">
        <section class="hero-content">
            <img src="../assets/logotype-horizontal-light.png" alt="Aternos" width="200" />

            <div>
                <h1>Aternos Games</h1>
                <h2>An <em>open-source</em>, <em>community-driven</em> and <em>ad-supported</em> Minecraft 1.13 network. Made by Aternos.</h2>
            </div>

            <p>&copy; 2018 Aternos UG (haftungsbeschränkt)</p>
        </section>
    </ag-container>

</template>

<style lang="scss" scoped>

    @import "../style/_breakpoints";

    section.hero-content {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        min-height: calc(100vh - 24px);

        @include for-desktop-up {
            min-height: calc(100vh - 48px);
        }

        h1 {
            color: #F0F0F0;
            font-size: 7vw;
            font-weight: 600;

            @include for-desktop-up {
                font-size: 3vw;
            }
        }

        h2 {
            color: #F0F0F0;
            font-size: 3vw;
            font-weight: 500;

            @include for-desktop-up {
                font-size: 1vw;
            }
        }
    }

</style>
