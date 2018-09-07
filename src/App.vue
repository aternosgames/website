<template>

    <div id="app">
        <router-view/>
    </div>

</template>

<style lang="scss">

    @import "style/_breakpoints";
    @import "style/_colors";
    @import "style/_fonts";

    * {
        margin: 0;
        padding: 0;

        &, &::after, &::before {
            box-sizing: border-box;
        }
    }

    html, body {
        height: 100%;
    }

    body {
        // background-color: $light;
        background-image: linear-gradient(165deg, $primary, $dark-primary);

        color: $dark;
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-size: 14px;
        font-style: normal;
        font-weight: 400;
        line-height: 1.42857142857143;
        overflow-x: hidden;
        -ms-overflow-style: -ms-autohiding-scrollbar;
        -webkit-text-decoration-skip: ink;
    }

    #app {
        min-height: 100vh;
        padding: env(safe-area-inset-top) env(safe-area-inset-right) env(safe-area-inset-bottom) env(safe-area-inset-left);
    }

</style>
