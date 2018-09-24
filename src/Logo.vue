<template>
    <div class="logo">
        <div class="logo__preview">
            <div class="automattic" :class="`automattic-${step}`"></div>
            <img class="logo__preview__img" src="./assets/logo.png">
            <div class="logo__preview__html">
                <pre v-highlightjs="html"><code class="html"></code></pre>
            </div>
        </div>
        <div class="logo__code">
            <div class="logo__code__outer">
                Outer
                <pre v-highlightjs="outer"><code class="css"></code></pre>
            </div>
            <div class="logo__code__inner">
                Inner
                <pre v-highlightjs="inner"><code class="css"></code></pre>
            </div>
        </div>
        <div class="logo__controls">
            <div class="logo__controls__back" @click="back">Back</div>
            <div class="logo__controls__next" @click="next">Next</div>
        </div>
    </div>
</template>

<script>
    const outer = {
        1: `width: 30vh;
    height: 30vh;`,
        2: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;`,
        3: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;
    border-radius: 100vh;`,
        4: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;
    border-radius: 100vh;
    transform: scaleY(0.92);`,
        5: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;
    border-radius: 100vh;
    transform: scaleY(0.92);`,
        6: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;
    border-radius: 100vh;
    transform: scaleY(0.92);
    position: relative;`,
        7: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;
    border-radius: 100vh;
    transform: scaleY(0.92);
    position: relative;`,
        8: `width: 30vh;
    height: 30vh;
    border: 5vh solid #2E99CE;
    border-radius: 100vh;
    transform: scaleY(0.92);
    position: relative;`,
    };

    const inner = {
        1: `content: "";`,
        2: `content: "";`,
        3: `content: "";`,
        4: `content: "";`,
        5: `content: "";
    width: 20%;
    height: 60%;
    display: block;
    background-color: #050708;`,
        6: `content: "";
    width: 20%;
    height: 60%;
    display: block;
    background-color: #050708;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);`,
        7: `content: "";
    width: 20%;
    height: 60%;
    display: block;
    background-color: #050708;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    border-radius: 100vh;`,
        8: `content: "";
    width: 20%;
    height: 60%;
    display: block;
    background-color: #050708;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%) rotate(30deg);
    border-radius: 100vh;`
    };

    export default {
        name: 'logo',

        data() {
            return {
                step: 1,
            }
        },

        computed: {
            html() {
              return `<div class="automattic"></div>`;
            },
            outer() {
                return `.automattic {
    ${outer[this.step]}
}`;
            },
            inner() {
                return `.automattic::before {
    ${inner[this.step]}
}`;
            },
        },

        methods: {
            next() {
                this.step++;
            },

            back() {
                this.step--;
            },
        },
    }
</script>

<style lang="scss">
    $black: #050708;
    $blue: #2E99CE;

    @import url('https://fonts.googleapis.com/css?family=Roboto');
    @import "../node_modules/highlight.js/styles/github.css";

    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        padding: 0;
        font-family: 'Roboto', sans-serif;
    }

    .logo {
        width: 100vw;
        display: flex;
        flex-direction: column;
    }

    .logo__preview {
        padding: 1rem;
        width: 100vw;
        height: 40vh;
        display: flex;
        position: relative;
        align-items: center;
        justify-content: center;
    }

    .logo__preview__html {
        position: absolute;
        bottom: 1px;
        left: 1rem;
    }

    .logo__preview__img {
        position: absolute;
        bottom: 1rem;
        right: 1rem;
    }

    .logo__code {
        width: 100vw;
        height: 60vh;
        display: flex;
        position: relative;
    }

    .logo__code__outer,
    .logo__code__inner {
        border-top: 5px solid $black;
        width: 50vw;
        padding: 1rem;
    }

    .logo__code__outer {
        border-right: 5px solid $black;
    }

    .logo__controls {
        position: absolute;
        top: 1rem;
        right: 1rem;
        display: flex;
    }

    .logo__controls__back,
    .logo__controls__next {
        padding: 0.5rem 1rem;
        border: 3px solid $black;
        cursor: pointer;

        &:hover {
            background-color: lighten($black, 80%);
        }
    }

    .logo__controls__next {
        border-left: none;
    }

    .automattic {
        &, &::before {
            transition: 1s;
        }
    }

    .automattic-1 {
        width: 30vh;
        height: 30vh;
        border: 0 solid transparent;

        &::before {
            content: "";
            position: absolute;
            left: 0;
            top: 0;
        }
    }

    .automattic-2 {
        @extend .automattic-1;
        border: 5vh solid $blue;
    }

    .automattic-3 {
        @extend .automattic-2;
        border-radius: 100vh;
    }

    .automattic-4 {
        @extend .automattic-3;
        transform: scaleY(0.92);
    }

    .automattic-5 {
        @extend .automattic-4;

        &::before {
            width: 20%;
            height: 60%;
            display: block;
            background-color: $black;
        }
    }

    .automattic-6 {
        @extend .automattic-5;
        position: relative;

        &::before {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translateX(-50%) translateY(-50%);
        }
    }

    .automattic-7 {
        @extend .automattic-6;

        &::before {
            border-radius: 100vh;
        }
    }

    .automattic-8 {
        @extend .automattic-7;

        &::before {
            transform: translateX(-50%) translateY(-50%) rotate(30deg);
        }
    }
</style>
