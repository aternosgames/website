<script lang="ts">

    import { Component, Prop, Vue } from "vue-property-decorator";

    @Component
    export default class AgNavigation extends Vue {

        @Prop(Boolean) private fluid!: boolean;

        @Prop(String) private scrollTarget!: string;

        private isScaled: boolean = false;

        mounted(): void {
            if (document.querySelector("a")) {
                document.querySelectorAll("a").forEach((el) => {
                    el.addEventListener("click", (ev) => {
                        ev.preventDefault();

                        (document.querySelector(`${el.getAttribute("href")}`) as HTMLElement).scrollIntoView({ behavior: "smooth" });
                    });
                });
            }

            if (this.scrollTarget && document.querySelector(this.scrollTarget)) {
                const nav = (document.querySelector("nav.ag-navigation") as HTMLElement);
                window.addEventListener("scroll", (ev) => {
                    const height = nav.offsetWidth < 600 ? 64 : nav.offsetHeight;
                    this.isScaled = window.scrollY >= ((document.querySelector(this.scrollTarget) as HTMLElement).offsetTop + (document.querySelector(this.scrollTarget) as HTMLElement).offsetHeight - height - 1);
                });
            }
        }

    }

</script>

<template>

    <nav :class="['ag-navigation', { scaled: isScaled }]">
        <section :class="['navigation-inner', { fluid: fluid }]">
            <div class="logos">
                <img src="../assets/logotype-horizontal-light.png" alt="Aternos" height="40" class="logo-wordmark" />
                <img src="../assets/logo-light.png" alt="Aternos" height="40" />
            </div>
            <slot />
        </section>
    </nav>

</template>

<style lang="scss" scoped>

    @import "../style/_breakpoints";
    @import "../style/_colors";

    nav.ag-navigation {
        height: 64px;
        position: fixed;
        transition: all .2s ease;
        width: 100%;
        z-index: 99999;

        @include for-desktop-up {
            height: 88px;
        }

        &.scaled {
            background-color: $primary;

            .logos {
                width: 40px;
            }

            img.logo-wordmark {
                clip-path: inset(0 0 0 100%);
                transform: translateX(-100%);
            }
        }
    }

    section.navigation-inner {
        align-items: center;
        display: flex;
        height: 100%;
        justify-content: space-between;
        margin: 0 auto;
        max-width: 1600px;
        padding: 0 12px;
        transition: all .2s ease;

        @include for-desktop-up {
            padding: 0 24px;
        }

        &.fluid {
            max-width: unset;
            width: 100%;
        }
    }

    .logos {
        height: 40px;
        position: relative;
        transition: all .4s ease;
        width: 200px;

        img {
            position: absolute;
            transition: all .4s ease, clip-path .3s ease;
        }

        img.logo-wordmark {
            clip-path: inset(0 0 0 48px);
        }
    }

    a {
        color: $light;
        font-family: metropolis;
        font-size: 15px;
        font-weight: 500;
        text-decoration: none;
        transition: all .4s ease;
    }

    @include for-phone-only {
        nav.ag-navigation {
            height: 115px;
            transition: all .2s ease, height .4s ease .4s;


            &.scaled {
                height: 64px;
            }

            a {
                margin: 9px 0;
            }
        }

        section.navigation-inner {
            flex-wrap: wrap;
            justify-content: space-around;
            padding: 12px;
        }

        .logos {
            margin: 0 calc(50% - 100px) 12px calc(50% - 100px);
            transition: all .4s ease, margin-top .4s ease .4s;

            .scaled & {
                margin: -52px calc(50% - 20px) 12px calc(50% - 20px);
            }
        }
    }

    @include for-tablet-portait-only {
        section.navigation-inner {
            justify-content: space-around;
        }

        .logos {
            order: 3;
        }

        @for $i from 1 through 4 {
            a:nth-of-type(#{$i}) {
                @if $i < 3 {
                    order: #{$i};
                }
                @else {
                    order: #{$i + 1};
                }
            }
        }
    }

    @include for-tablet-landscape-only {
        section.navigation-inner {
            justify-content: space-around;
        }

        .logos {
            order: 3;
        }

        @for $i from 1 through 4 {
            a:nth-of-type(#{$i}) {
                @if $i < 3 {
                    order: #{$i};
                }
                @else {
                    order: #{$i + 1};
                }
            }
        }
    }

</style>