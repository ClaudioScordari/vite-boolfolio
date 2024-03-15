<script>
import axios from 'axios';

export default {
    data() {
        return {
            project: null,
        }
    },
    created() {
        this.getDatas();
    },
    methods: {
        getDatas(){
            axios  
                .get('http://127.0.0.1:8000/api/projects/' + this.$route.params.id)
                .then(response => {
                    // dentro la variabile cè il contenuto della chiamata api al singolo project 
                    // console.log(response.data);
                    this.project = response.data.response;
                });
        },
    }
}
</script>

<template>
    <div v-if="project != null" class="d-flex justify-content-center align-items-center container pt-5 ">
        <div  class="card" style="width: 40%;">
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
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>
