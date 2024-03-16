<script>
// Axios
import axios from 'axios';

export default {
    data() {
        return {
            name: '',
            email: '',
            message: '',
            accepted: false,
        }
    },
    methods: {
        sendMessage(){
            if (
                this.name != null
                &&
                this.name != ''
                &&
                this.name.length <= 64
                &&
                this.email != null
                &&
                this.email != ''
                &&
                this.name.length <= 255
                &&
                this.message != null
                &&
                this.message != ''
                &&
                this.message.length <= 1000
                &&
                this.accepted
            ) {
                // Chiamata api per inviare i dati
                axios
                    .post('http://127.0.0.1:8000/api/contacts',{

                        // Invio delle variabili - chiave: variabile
                        name: this.name,
                        email: this.email,
                        message: this.message,
                        accepted: this.accepted,
                    })
                    .then(res => {
                        console.log('risposta', res.data)
                    });
            }
            else {
                alert('Iserisci bene gli input')
            }
        },
    }
}
</script>

<template>
    <h1>
        Pagina contatti
    </h1>

    <div class="container">
        <h2>Invia un messaggio</h2>

        <!-- Form -->
        <form @sumbmit.prevent="sendMessage()" method="POST">

            <!-- Input del nome del contatto -->
            <div class="box-name mb-3">
                <label class="d-block" for="name">Nome <span class="text-danger">*</span></label>
                <input type="text" required maxlength="64" id="name" name="name" v-model="name" placeholder="Inserisci il nome">
            </div>

            <!-- Input dell'email -->
            <div class="box-email mb-3">
                <label class="d-block" for="email">Email <span class="text-danger">*</span></label>
                <input type="email" required maxlength="255" id="email" name="email" v-model="email" placeholder="Inserisci l'email">
            </div>

            <!-- Input del messaggio -->
            <div class="box-message mb-3">
                <label class="d-block" for="message">Messaggio <span class="text-danger">*</span></label>
                <textarea v-model="message" maxlength="1000" name="message" id="message" cols="25" rows="5" placeholder="Inserisci il messaggio" required></textarea>
            </div>

            <!-- Input "Accetto i termini e le condizoni" -->
            <div class="box-accepted mb-3">
                <input v-model="accepted" type="checkbox" name="accepted" id="accepted" required>
                <span  class="d-inline-block ms-2 text-danger">*</span>
                <label class="d-inline-block ms-1" for="accepted">Accetta i <a href="#">Termini e condizoni</a></label>
            </div>

            <!-- Campi obbligatori -->
            <p class="fs-6">I campi contrassegnati con <span class="text-danger">*</span> sono obbligatori</p>

            <button type="submit" class="btn btn-primary">
                Invia
            </button>
        </form>
    </div>
</template>

<style scoped>
h1{
    text-align: center;
}
</style>
