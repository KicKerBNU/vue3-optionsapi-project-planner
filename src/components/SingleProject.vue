<template>
    <div class="space"></div>
    <div class="card project" :class="{ complete: project.complete }">
        <div class="row no-wrap middle-align">
            <details>
                <summary class="none">
                    <div>{{project.title}}</div>
                </summary>
                <p>{{project.details}}</p>
            </details>
            <div class="col min">
                <nav>
                    <router-link :to="{ name: 'EditProject', params: { id: project.id}}">
                        <a>
                            <i class="material-icons">edit</i>
                        </a>
                    </router-link>
                        
                    <a>
                        <i class="material-icons" @click="deleteProject">delete</i>
                    </a>
                    <a>
                        <i class="material-icons" :class="{ 'tick': project.complete }" @click="toggleComplete">done</i>
                    </a>
                </nav>  
            </div>
        </div>
            
    </div>
    
</template>

<script>
export default {
    props: {
        project: Object,
    },
    data() {
        return {
            uri: 'http://localhost:3000/projects/' + this.project.id
        }
    },
    methods: {
        toggleComplete() {
            fetch(this.uri, { 
                method: 'PATCH',
                headers: { 'Content-Type': 'application/json'},
                body: JSON.stringify({ complete: !this.project.complete})
            }).then(() => {
                this.$emit('complete', this.project.id);
            }).catch((e) => {
                console.log(e);
            })
        },
        deleteProject() {
            fetch(this.uri, { method: 'DELETE'})
            .then(() => {
                this.$emit('delete', this.project.id);
            }).catch(e => {
                console.log(e);
            })
        }
    },
}
</script>

<style scoped>
 .project {
     border-left: 4px solid #e90074;
 }
 .complete {
     border-left: 4px solid #00ce89;
 }
 .tick{
    color: #00ce89;
 }
</style>