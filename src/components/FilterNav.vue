<template>
  <nav class="filter-nav">
      <a class="chip" @click="updateFilter('all')">
          <i class="small" v-show="current === 'all'">done</i>All
      </a>
      <a class="chip" @click="updateFilter('completed')">
          <i class="small" v-show="current === 'completed'">done</i>Completed
      </a>
      <a class="chip" @click="updateFilter('ongoing')">
          <i class="small" v-show="current === 'ongoing'">done</i>Ongoing
      </a>
  </nav>
</template>

<script>
export default {
    props: {
        current: String
    },
    methods: {
        updateFilter(by) {
            this.$emit('filterChange', by);
        }
    },
}
</script>

<style>

</style>