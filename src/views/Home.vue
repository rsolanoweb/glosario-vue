<template>
    <div>
        <div class="letter" v-for="i in letters" v-if="i.words.length !== 0">
            <hr>
            <h2 class="title is-3 has-text-centered">Palabras con la {{i.name}}</h2>
            <div class="word" v-for="w in i.words">
                <h2 class="title is-4">{{w.name}}</h2>
                <div class="body">
                    <div class="body-content" v-html="w.description"></div>
                    <div class="fuente" v-if="w.sources">
                        <p>
                            Referencias: <a :href="w.sources" target="_blank" style="word-break: break-all">{{w.sources.slice(0, 50)}}{{ w.sources.length > 50 ? '...' : ''}}</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'home',
        data() {
            return {
                letters: []
            }
        },
        mounted() {
            axios.get('https://glosario-app.herokuapp.com/api/words/').then(response => (
                this.letters = response.data
            ));
        },
    }
</script>

<style lang="scss" scoped>
    hr {
        margin: 3.5rem 0;
    }

    .title.is-4 {
        background-color: #fafafa;
        margin: 0;
        padding: .25em .5em;
    }

    .body {
        font-size: 1.25em;
        padding: .5em;
        margin-top: 1em;
        margin-bottom: 2em;

        .fuente {
            border-left: 4px solid rgba(66, 133, 244, 0.2);
            padding-left: .75em;
            margin-top: 1.25em;
            font-size: .85em !important;
        }
    }
</style>
