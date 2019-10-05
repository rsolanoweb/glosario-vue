<template>
    <transition name="fade">
        <div class="preload" v-if="show">
            <div class="spinner"></div>
        </div>
    </transition>
</template>

<script>
    export default {
        name: "Preloader",
        data() {
            return {
                show: true
            }
        },
        mounted() {
            this.showToggle()
        },
        methods: {
            showToggle() {
                setTimeout(() => {
                    this.show = false
                }, 1000)
            }
        }
    }
</script>

<style scoped>
    .preload {
        position: fixed;
        width: 100vw;
        height: 100vh;
        background-color: #fff;
        z-index: 10000;
        left: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        overflow-x: hidden;
        top: 0;
    }

    .spinner {
        width: 120px;
        height: 120px;
        border-top: .5em solid #4285f4;
        border-left: .5em solid #4285f422;
        border-right: .5em solid #4285f422;
        border-bottom: .5em solid #4285f422;
        border-radius: 50%;
        background-color: #fff;
        animation: spinner 1s infinite alternate ease-in-out;
    }

    @keyframes spinner {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(300deg);
        }
    }

    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to {
        opacity: 0;
    }

    h1 {
        color: #fff;
    }
</style>
