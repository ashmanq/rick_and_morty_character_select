<template lang="html">
  <div class="">
    <select v-model="selectedOption" v-on:change="handleSelect" id="characters">
      <list-option v-for="(character, index) in characters" :character="character" :key="index"></list-option>
    </select>
  </div>
</template>

<script>

import ListOption from './ListOption.vue';
import {eventBus} from '../main.js';

export default {
  name: 'character-list',
  props: ['characters'],
  data() {
    return {
      selectedOption: null,
    }
  },
  methods: {
    handleSelect: function(){
      const selectedCharacter = this.characters.find((character) => {
        return character.name === this.selectedOption;
      });
      eventBus.$emit('character-selected', selectedCharacter);
    }
  },
  components: {
    "list-option": ListOption
  }
}
</script>

<style lang="css" scoped>
</style>
