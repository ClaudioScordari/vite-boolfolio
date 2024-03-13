<script>
import axios from 'axios';

export default {
    data() {
        return {
            datas: [],
        }
    },
    created() {
        axios  
            .get('http://127.0.0.1:8000/api/projects')
            .then(response => {
                console.log(response.data.response.data);
            });
    }
}
</script>

<template>
    <h1>
        Componente principale
    </h1>

    <div class="main-content">

    </div>
</template>

<style scoped>
</style>
