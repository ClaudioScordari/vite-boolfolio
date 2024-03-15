<script>
import axios from 'axios';

export default {
    data() {
        return {
            datas: [],
            currentPage: 1,
            lastPage: 1,
        }
    },
    created() {
        this.getDatas(this.currentPage);
    },
    methods: {
        getDatas(page){
            axios  
                .get('http://127.0.0.1:8000/api/projects',{
                    params: {
                        page: page,
                    }
                })
                .then(response => {
                    // console.log(response.data.response);

                    // Array con tutti i dati 
                    this.datas = response.data.response.data;

                    // Imposto il valore della pagina corrente e dell'ultima
                    this.currentPage = response.data.response.current_page
                    this.lastPage = response.data.response.last_page
                    // console.log(this.currentPage, this.lastPage)
                });
        },
        nextPage(){
            if (this.currentPage < this.lastPage) {

                this.getDatas(this.currentPage + 1);
            }
        },
        prevPage(){
            if (this.currentPage > 1) {

                this.getDatas(this.currentPage - 1);
            }
        },
    }
}
</script>

<template>
    <div class="d-flex justify-content-between container pt-5">
        <div  class="card" style="width: calc((100% / 4) - 15px);"  v-for="project in datas" >
           <img class="card-img-top" :src="'http://127.0.0.1:8000/storage/' + project.image_src" :alt="project.name">
    
            <div class="card-body">
                <h5 class="card-title">
                    <span>
                        {{ project.id }})
                    </span>
    
                    {{ project.name }}
                </h5>
    
                <p class="card-text">
                    {{ project.description }}
                </p>
    
                <a href="#" class="btn btn-primary">Vedi</a>
            </div>
        </div>
    </div>

    <div class="container box-buttons mt-4 d-flex justify-content-around">
        <button @click="prevPage()" class="btn btn-primary" type="submit">Indetro</button>
        <button @click="nextPage()" class="btn btn-primary" type="submit">Avanti</button>
    </div>
</template>

<style scoped>
</style>
