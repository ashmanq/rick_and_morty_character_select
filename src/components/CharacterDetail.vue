<template lang="html">
  <div class="char-details">
      <h3>{{character.name}}</h3>
      <p>Name: {{character.name}}</p>
      <p>Gender: {{character.gender}}</p>
      <p>Species: {{character.species}}</p>
      <p>Status: {{character.status}}</p>
      <p>Origin: {{ character.origin.name }}</p>
      <img v-bind:src="character.image"></img>
  </div>
</template>

<script>
export default {
  name: 'character-detail',
  props: ['character']
}
</script>

<style lang="css" scoped>
  .char-details {
    text-align: center;
  }
  img {
    border-radius: 3px;
    border-width: 8px;
    border-style: solid;
    margin-top:30px;
    border-color: #519c44;
  }

  p {
    margin: 10px 0px;
  }
</style>
