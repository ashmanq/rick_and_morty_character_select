<template lang="html">
  <div class="">
    <label for="search">Search</label>
    <input v-model="searchQuery" v-on:input="handleSearch" type="text" name="search" placeholder="Type to start search">
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name:'search',
  data() {
    return {
      searchQuery: null,

    }
  },
  methods: {
    handleSearch: function() {
      eventBus.$emit('search-query', this.searchQuery)
    }
  }
}
</script>

<style lang="css" scoped>

  label, input {
    font-size: 1.2em;
    margin:10px;
    border-radius: 5px;
    text-align: center;
  }

</style>
