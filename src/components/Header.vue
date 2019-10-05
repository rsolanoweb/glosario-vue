<template>
    <div>
        <nav>
            <div class="columns" style="margin-top: 0">
                <div class="column is-10">
                    <img src="../assets/logo.png" alt="logo" width="150" style="margin-bottom: -5px"/>
                    <h1 class="title is-5 is-inline-block"
                        style="border-left: .15em solid #4285f4; padding-left: .75rem; font-weight: 500; margin-left: .75em">
                        Glosario de Rubén</h1>
                </div>
                <div class="column is-2 has-text-right">
                    <a class="button is-primary" href="https://glosario-app.herokuapp.com/admin" target="_blank">
                        <strong>Admin</strong>
                    </a>
                </div>
            </div>
            <div class="tabs is-toggle is-fullwidth">
                <ul>
                    <li :class="{'is-active': this.$route.path === '/'}">
                        <router-link to="/" style="padding: 0.45em .5em;">
                            <span>*</span>
                        </router-link>
                    </li>
                    <li v-for="i in letters" :class="{'is-active': $route.params.letter === i}">
                        <router-link :to="{ name: 'letter', params: { letter: i }}" style="padding: 0.45em .5em;">
                            <span :key="i">{{i}}</span>
                        </router-link>
                    </li>
                </ul>
            </div>
        </nav>
        <nav class="navbar is-fixed-top navbar-tabs" :class="{'navbar-tabs-active': scrollPosition > 177, 'navbar-tabs-hide': scrollPosition < 177}">
            <div class="container">
                <div class="tabs is-toggle is-fullwidth">
                    <ul>
                        <li :class="{'is-active': this.$route.path === '/'}">
                            <router-link to="/" style="padding: 0.45em .5em;">
                                <span>*</span>
                            </router-link>
                        </li>
                        <li v-for="i in letters" :class="{'is-active': $route.params.letter === i}">
                            <router-link :to="{ name: 'letter', params: { letter: i }}" style="padding: 0.45em .5em;">
                                <span :key="i">{{i}}</span>
                            </router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data() {
            return {
                letters: 'abcdefghijklmnñopqrstuvwxyz'.split(""),
                scrollPosition: null
            }
        },
        methods: {
            updateScroll() {
                this.scrollPosition = window.scrollY;
            }
        },
        mounted() {
            window.addEventListener('scroll', this.updateScroll);
        },
        destroyed() {
            window.removeEventListener('scroll', this.updateScroll);
        }
    }
</script>

<style scoped>
    /* Media Queries */
    @media (max-width: 768px) {
        .button.is-primary {
            width: 100%;
        }

        .title.is-5 {
            margin-left: 0 !important;
            margin-top: .25em !important;
            padding-left: 0.5rem !important;
        }

        .navbar-tabs > .container {
            width: auto !important;
        }

        .navbar-tabs .tabs {
            padding: 1rem !important;
        }
    }
</style>
