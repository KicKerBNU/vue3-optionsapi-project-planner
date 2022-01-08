<template>
<div class="menu m l top">
    <a>
        <router-link :to="{ name: 'Home' }" :class="active">Projects</router-link>
    </a>
    <a>
        <router-link :to="{ name: 'AddProject'}">New Project</router-link>
    </a>
</div>
</template>

<script>
export default {

}
</script>

<style>
a.router-link-active {
    border-bottom: 2px solid #00ce89;
}
</style>