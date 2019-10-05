<template>
    <div id="app">
        <Preloader />
        <section class="section">
            <div class="container">
                <div class="container has-background-white"
                     style="box-shadow: 0 16px 128px 0 rgba(69,75,92,0.3); padding: 1rem 1.75rem; border-radius: 4px;">
                    <Header/>
                    <div class="main-content">
                        <router-view :key="this.$route.fullPath"/>
                    </div>
                    <Footer/>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    import Header from '@/components/Header'
    import Footer from '@/components/Footer'
    import Preloader from '@/components/Preloader'

    export default {
        name: 'home',
        components: {
            Header,
            Footer,
            Preloader
        },
        data() {
            return {
                showInfo: true
            }
        }
    }
</script>


<style lang="scss" scoped>
    .slide-fade-enter-active {
        transition: all .3s ease;
    }
    .slide-fade-leave-active {
        transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }
    .slide-fade-enter, .slide-fade-leave-to
        /* .slide-fade-leave-active below version 2.1.8 */ {
        transform: translateX(10px);
        opacity: 0;
    }

    .main-content {
        margin: 2em 0;
    }
</style>
