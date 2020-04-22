<template lang="html">
    <option v-bind:value="character.name">{{ character.name }}</option>
</template>

<script>



export default {
  name: 'list-option',
  props: ['character']
  // methods: {
  //   handleClick() {
  //     eventBus.$emit('character-option-selected', this.character);
  //   }
  // }
}
</script>

<style lang="css" scoped>
</style>
