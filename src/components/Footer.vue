<template>
    <footer>
        © {{new Date().getFullYear()}}, Glosario de <a href="https://rsolanoweb.now.sh/">Rubén Solano</a>
    </footer>
</template>

<script>
    export default {
        name: "Footer"
    }
</script>

<style scoped>
    footer {
        margin-top: 4rem;
    }
</style>
