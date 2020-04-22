<template lang="html">
  <div class="">
    <h1>Rick And Morty Character Search App</h1>
    <div class="container">
      <section class="selection">
        <character-search></character-search>
      </section>
      <section class="details">
        <character-detail v-if="selectedCharacter" :character="selectedCharacter"></character-detail>
        <p v-if="!selectedCharacter">Wubba Lubba Dub-Dub! Keep Searching!</p>
      </section>
    </div>
  </div>
</template>

<script>

import CharacterList from './components/CharacterList.vue';
import CharacterDetail from './components/CharacterDetail.vue';
import Search from './components/Search.vue';
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
    // Code that recieves everytime a new letter is entered into the search bar
    eventBus.$on('search-query', (searchQuery) => {
      if(searchQuery!==""){
      // We use find to return the first result from a check to wee which character
      // names include the search query
      this.selectedCharacter = this.characters.find((character) => {
        return character.name.toLowerCase().includes(searchQuery.toLowerCase());
      })
    } else {
      this.selectedCharacter = null;
    };
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
    "character-detail": CharacterDetail,
    "character-search": Search
  }
}
</script>

<style lang="css" scoped>

  h1 {
      font-family: 'schwifty';
      font-size: 3em;
      text-align: center;
      margin:40px;
  }


  .container {
    display: flex;
    flex-direction: column;
    /* justify-content: space-between; */
    font-size: 1.5em;
    font-family:sans-serif, "Verdana";
  }

  .selection {
    display: flex;
    flex-direction: column;
    align-self: center;
    align-items: center;
    margin: 20px;
    width:50%;
  }

  .details {
    display: flex;
    flex-direction: column;
    align-self: center;
    align-items: center;
    /* margin: 10px; */
    width:50%;

    background-color: #f4f484;
    margin: 20px 0px;
    padding: 20px 10px;
    border-radius: 3px;
  }

  @media only screen and (max-width: 900px){
      .container {
        flex-direction: column;
      }
      .selection {
        text-align: center;
        margin:5px 5px;
        width:90%;
      }
      .details {
        width: 90%;
      }

  }

</style>
