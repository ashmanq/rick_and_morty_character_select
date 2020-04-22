<template lang="html">
  <div>
      <h3>{{character.name}}</h3>
      <p>Name: {{character.name}}</p>
      <p>Gender: {{character.gender}}</p>
      <p>Species: {{character.species}}</p>
      <p>Status: {{character.status}}</p>
  </div>
</template>

<script>
export default {
  name: 'character-detail',
  props: ['character']
}
</script>

<style lang="css" scoped>
</style>
