<template>
  <div class="container">
        <div class="card large">
            <h5>Edit Project</h5>
            <form @submit.prevent="handleEdit">
                <div class="field label">
                    <input type="text" required v-model="title">
                    <label>Title</label>
                </div>
                <div class="field textarea label">
                    <textarea required v-model="details"></textarea>
                    <label>Details</label>
                </div>
                <div class="center-align">
                    <button>Update Project</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import { nextTick } from 'vue'
export default {
    data() {
        return {
            title: '',
            details: '',
            uri: 'http://localhost:3000/projects/'+this.id
        }
    },
    props: {
        id: Number
    },
    mounted () {
        fetch(this.uri)
        .then(response => response.json())
        .then(data =>{
            this.title = data.title;
            this.details = data.details;
            nextTick(() => {
                ui();
            })
        });
    },
    methods: {
        handleEdit() {
            fetch(this.uri, { 
                method: 'PATCH',
                headers: { 'Content-Type': 'application/json'},
                body: JSON.stringify({ title: this.title, details: this.details})
            }).then(() => {
                this.$router.push('/');
            }).catch((e) => {
                console.log(e);
            })
        }
    },

}
</script>

<style>

</style>