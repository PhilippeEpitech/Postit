<template>
    
    <main>
        <div v-for="notes in note" v-bind:key="notes.name">
            <div v-if="notes.id == $route.params.id">

                    <div class="container">
                        <textarea class="note" v-model="notes.name" @input="listeners(notes)">Some sample text</textarea>
                        
                        <button class="retour"><router-link to="/">Retour</router-link></button>
                    </div>

            </div>
        </div>

    </main>

</template>

<script>
export default {
    name: 'Post',
    data() {
        return {
            note: JSON.parse(localStorage.getItem('note'))
        }
    },
    
    props: ['id']
}

</script>t

<style scoped>
.note {
    border: 2px solid black;
    border-radius: 20px;
    width: 600px;
    height: 400px;
    padding: 10px;
    margin: 10px;
    text-align: center;
    background-color: rgba(255, 220, 0, 0.5 );
    margin-left: 280px;
    color:black;
    font-family: sans-serif;
    font-size: 1.5rem;

}

.retour {
    margin-left: 550px;
}

</style>