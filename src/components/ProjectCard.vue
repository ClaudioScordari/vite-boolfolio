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
                // console.log(response.data.response);

                // Array con tutti i dati 
                this.datas = response.data.response;
                console.log(this.datas);
            });
    },
}
</script>

<template>
    <div  class="card" style="width: calc((100% / 4) - 15px);"  v-for="project in datas" >
       <img class="card-img-top" :src="'http://127.0.0.1:8000/storage/' + project.image_src" :alt="project.name">

        <div class="card-body">
            <h5 class="card-title">
                {{ project.name }}
            </h5>

            <p class="card-text">
                {{ project.description }}
            </p>

            <a href="#" class="btn btn-primary">Vedi</a>
        </div>
    </div>
</template>

<style scoped>
</style>
