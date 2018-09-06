<script lang="ts">

    import { Component, Vue } from "vue-property-decorator";

    import AgContainer from "@/components/AgContainer.vue";
    import AgNavigation from "@/components/AgNavigation.vue";

    @Component({
        components: {
            AgContainer,
            AgNavigation
        },
    })
    export default class Home extends Vue {}

</script>

<template>

    <div class="page">

        <ag-navigation scrollTarget="#hero">
            <a href="#about">About</a>
            <a href="#financing">Financing</a>
            <a href="#team">Team</a>
            <a href="#roadmap">Roadmap</a>
        </ag-navigation>

        <ag-container id="hero">
            <section class="hero-content">
                <div>
                    <h1>Aternos Games</h1>
                    <h2>An <em>all open-source</em>, <em>international</em>, <em>community-driven</em> and <em>ad-supported</em> Minecraft 1.13 network. Made by Aternos.</h2>
                </div>
            </section>
        </ag-container>

        <section id="about" class="promo">
            <ag-container>
                <article class="promo-article">
                    <h1>About</h1>
                    <p>Open-Source, international, community-driven</p>
                </article>
            </ag-container>
        </section>

        <section id="financing" class="promo">
            <ag-container>
                <article class="promo-article">
                    <h1>Financing</h1>
                    <p>Ad-supported</p>
                </article>
            </ag-container>
        </section>

        <section id="team" class="promo">
            <ag-container>
                <article class="promo-article">
                    <h1>Team</h1>
                    <p>Matthias, dahendriik, Mvmo, Schwedifiziert, Shad0wCore</p>
                </article>
            </ag-container>
        </section>

        <section id="roadmap" class="promo">
            <ag-container>
                <article class="promo-article">
                    <h1>Roadmap</h1>
                    <p>TBA</p>
                </article>
            </ag-container>
        </section>

        <ag-container class="footer">
            <p>&copy; 2018 Aternos</p>
        </ag-container>

    </div>

</template>

<style lang="scss" scoped>

    @import "../style/_breakpoints";
    @import "../style/_colors";

    section.hero-content {
        display: flex;
        flex-direction: column;
        justify-content: center;
        min-height: calc(100vh - 24px);

        @include for-desktop-up {
            min-height: calc(100vh - 48px);
        }

        h1 {
            color: $light;
            font-family: metropolis;
            font-size: 50px;
            font-weight: 800;
        }

        h2 {
            color: $light;
            font-size: 19px;
            font-weight: 500;
        }
    }

    section.promo {
        background-color: $light;
        box-shadow: 0 0 10px 1px rgba(0, 0, 0, .2);

        // demo
        min-height: 50vh;
    }

    article.promo-article {
        color: $dark;
        padding: 2em 0;

        h1 {
            color: $primary;
            font-family: metropolis;
            font-size: 32px;
            font-weight: 700;
            margin-bottom: .5em;
        }
    }

    .footer {
        color: $light;
    }

</style>
