<script>
// Importazione componenti
import ProjectCard from './ProjectCard.vue';

export default {
    data() {
        return {

        }
    },
    components: {
        ProjectCard
    },
}
</script>

<template>
    <h1>
        Componente principale
    </h1>

    <div class="main-content container d-flex justify-space-between gap-3 flex-wrap">
        <ProjectCard />
    </div>
</template>

<style scoped>
</style>
