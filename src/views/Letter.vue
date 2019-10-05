<template>
    <div>
        <div class="letter" v-for="i in oneLetter" :key="i.name">
            <hr>
            <h2 class="title is-3 has-text-centered">Palabras con la {{i.name}}</h2>
            <div class="word" v-for="w in i.words" :key="w.name">
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
            <div v-if="i.words.length === 0">
                <h1 class="subtitle is-2 has-text-centered">¡No hay palabras que empiecen con la {{i.name}}! 😔</h1>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: "Letter",
        data() {
            return {
                letters: [],
                letter: this.$route.params.letter.toUpperCase()
            }
        },
        methods: {
            isLetter: function () {
                const alphabet = 'abcdefghijklmnñopqrstuvwxyz'.split('');
                const letter = this.$route.params.letter;

                if (alphabet.indexOf(letter) === -1) {
                    this.$router.push('/');
                }
            }
        },
        created() {
            this.isLetter();
        },
        mounted() {
            axios.get('https://glosario-app.herokuapp.com/api/words/').then(response => (
                this.letters = response.data
            ));
        },
        computed: {
            oneLetter: function() {
                return this.letters.filter((i) => {
                    return i.name === this.letter;
                });
            }
        }
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

