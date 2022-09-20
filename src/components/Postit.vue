<template>
    <div class="container">
        <div id="app">
            <div :key="notes.id" v-for="notes in note">
                <div>
                    <textarea class="note" v-model="notes.name" @input="listeners(notes)"></textarea>
                    

                    <button><router-link :to="{ name: 'Post', params: { id: notes.id } }">Suite</router-link></button>

                    
                    <button @click="deleteNote(notes)">x</button>
                </div>
            </div>
        </div>

        <div id="add-btn">
            <button class="add-note" @click="AddNote" type="button">Create a note</button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        note: Array,
    },
    data() {
        return {
            note: JSON.parse(localStorage.getItem('note')) ?? [],
            newNote: null,
        };
    },
    methods: {
        listeners(notes) {
            localStorage.setItem('note', JSON.stringify(this.note));
        },

        AddNote() {
            console.log(this.note);
            this.note.push({ id: this.note.length, name: '' });
            localStorage.setItem('note', JSON.stringify(this.note));
            this.note = JSON.parse(localStorage.getItem('note'));
            this.save.note();
        },

        updateValue(name) {
            this.$emit('input', name);
        },

        deleteNote: function (notes) {
            this.note.splice(this.note.indexOf(notes), 1);
            localStorage.setItem('note', JSON.stringify(this.note));
        },

        mounted() {},
    },
};
</script>

<style scoped>
button {
    color: black;
 }
.container {
    margin: 0;
    width: 1440px;
    height: auto;
    
}

#add-btn {
    padding-left: 70px;
}

#app {
    display: grid;
    grid-template-columns: repeat(auto-fill, 250px);
    padding: 24px;
    gap: 24px;
    
}
.note {
    height: 200px;
    box-sizing: border-box;
    padding: 16px;
    /* box-shadow: 0 0 7px rgba(0, 0, 0, 0.15); */
    resize: none;
    font-family: sans-serif;
    background-color: rgba(255, 220, 0, 0.5 );
    font-size: 16px;
    border: 2px solid black;
    border-radius: 20px;
    z-index: 1;
    }

</style>
