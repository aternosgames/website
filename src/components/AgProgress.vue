<script lang="ts">

    import { Component, Prop, Vue } from "vue-property-decorator";

    import Step from "../script/Step";

    @Component
    export default class AgProgress extends Vue {
        @Prop(Array) private steps!: Step[];

        mounted(): void {
            if (document.querySelector("div.step.completed")) {
                const elements = document.querySelectorAll("div.step.completed");
                for (let i = 0; i < elements.length - 1; i++) {
                    (elements[i] as HTMLElement).classList.add("previous");
                }

                (elements[elements.length - 1] as HTMLElement).classList.add("current");
            }
        }

        get stepWidth(): string {
            return `${100 / this.steps.length}%`;
        }
    }


</script>

<template>

    <div class="ag-progress">
        <div class="steps">
            <div v-for="step in this.steps" :key="step.id" :class="['step', { completed: step.completed }, { wip: step.wip }]" :style="{ width: stepWidth }">
                <div class="indicator"></div>
                <p class="title">{{ step.title }}</p>
                <p>{{ step.description }}</p>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>

    @import "../style/_breakpoints";
    @import "../style/_colors";

    .ag-progress {
        width: 100%;
    }

    .steps {
        display: flex;
        flex-wrap: wrap;
    }

    .step {
        align-content: flex-start;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin-bottom: 4em;
        min-width: 100%;

        &.completed {
            &:first-of-type .indicator {
                margin-left: 50%;
                width: 50%;

                &::after {
                    content: "↦";
                }
            }

            &:first-of-type.current .indicator {
                margin: 0 auto;
                width: 8px;

                &::after {
                    visibility: hidden;
                }
            }

            &:last-of-type .indicator, &.current .indicator {
                margin-right: 50%;
                width: 50%;

                &::after {
                    content: "⇥" !important;
                    left: unset !important;
                    right: -2px;
                    transform: none !important;
                }
            }

            &:not(:first-of-type) .indicator {
                border-bottom-left-radius: 0px;
                border-top-left-radius: 0px;

                &::after {
                    content: "→";
                    left: 50%;
                    transform: translateX(-50%);
                }
            }

            &.previous .indicator {
                border-bottom-right-radius: 0px;
                border-top-right-radius: 0px;
            }

            &.current p.title {
                color: $primary;
            }

            p.title {
                color: $dark;
                font-weight: 600;
            }
        }
    }

    p {
        margin: 1.5em 1em 0;
        text-align: center;
        width: 100%;

        &.title {
            color: #CCC;
        }
    }

    .indicator {
        background-color: #CCC;
        border-radius: 8px;
        height: 8px;
        margin: 0 auto;
        position: relative;
        width: 8px;

        &::after {
            color: $primary;
            font-size: 2em;
            left: -2px;
            position: absolute;
            top: -1.25em;
        }

        .completed & {
            background-color: $primary;
            width: 100%;
        }

        .wip & {
            background: repeating-linear-gradient(-45deg, $primary, $primary 1em, lighten($primary, 40%) 1em, lighten($primary, 40%) 2em);
        }
    }

    @include for-tablet-landscape-up {
        .step {
            min-width: 50%;
        }
    }

    @include for-desktop-up {
        .step {
            min-width: 25%;
        }

        .indicator::after {
            visibility: hidden;
        }
    }

</style>