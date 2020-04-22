<template lang="html">
  <div class="container">
    <section>
      <h1>Rick And Morty Character List App</h1>
      <character-list :characters='characters'></character-list>
    </section>
    <section>
      <character-detail v-if="selectedCharacter" :character="selectedCharacter"></character-detail>
    </section>
  </div>
</template>

<script>

import CharacterList from './components/CharacterList.vue';
import CharacterDetail from './components/CharacterDetail.vue';
import {eventBus} from './main.js';

export default {
  name:'app',
  data(){
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  mounted(){
    this.fetchCharacters();

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },

  methods: {
    fetchCharacters: function() {
      fetch('https://rickandmortyapi.com/api/character/')
      .then(response => response.json())
      .then(data => this.characters = data.results);
    },
  },
  components: {
    "character-list": CharacterList,
    "character-detail": CharacterDetail
  }
}
</script>

<style lang="css" scoped>

  .container {
    display: flex;
    justify-content: space-between;
  }

</style>
