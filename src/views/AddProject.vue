<template>
    <div class="container">
        <div class="card large">
            <h5>Create Project</h5>
            <form @submit.prevent="handleSubmit">
                <div class="field label">
                    <input type="text" required v-model="title">
                    <label>Title</label>
                </div>
                <div class="field textarea label">
                    <textarea required v-model="details"></textarea>
                    <label>Details</label>
                </div>
                <div class="center-align">
                    <button>Add Project</button>
                </div>
            </form>
        </div>
    </div>
    
</template>

<script>
export default {
    data() {
        return {
            title: '',
            details: ''
        }
    },
    methods: {
        handleSubmit() {
            let project = {
                title: this.title,
                details: this.details,
                complete: false
            }
            fetch('http://localhost:3000/projects', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(project)
            }).then(() => {
                this.$router.push('/');
            }).catch(e => {
                console.log(e);
            })
        }
    },
    mounted () {
        ui();
    },
}
</script>

<style>

</style>