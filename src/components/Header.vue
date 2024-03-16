<script>
export default {
    data() {
        return {

        }
    },
}
</script>

<template>
    <header class="d-flex justify-content-around p-4 bg-primary text-light">
        <div class="logo-box">
            <router-link class="px-3 py-4 text-light" :to="{ name: 'home' }">
                Logo
            </router-link>
        </div>

        <div class="nav-box">
            <nav>
                <router-link class="px-3 py-4 text-light" :to="{ name: 'home' }">
                    Home
                </router-link>
                
                <router-link class="px-3 py-4 text-light" :to="{ name: 'projects.index' }">
                    Progetti
                </router-link>

                <router-link class="px-3 py-4 text-light" :to="{ name: 'contacts' }">
                    Contatti
                </router-link>
            </nav>
        </div>
    </header>
</template>

<style scoped>
</style>
