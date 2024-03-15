<script>
// Importazioni componenti
import Main from './components/Main.vue';
import Header from './components/Header.vue';

export default {
    data() {
        return {
        
        }
    },
    components: {
        Header,
        Main,
    },
}
</script>

<template>
    <Header />

    <Main />

    <footer>
        Footer App
    </footer>
</template>

<style scoped>
</style>
