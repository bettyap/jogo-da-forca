<template>
  <div class="keyboard-container">

    <button 
      class="keyboard-button" 
      v-for="(letter, key) in 'aáàâãbcçdeéèêfghiíjklmnoóôõpqrstuúvwxyz'"
      :key="key"
      :disabled="verificarLetra(letter)"
      @click="jogar(letter)"
    >
      {{letter}}
    </button>

  </div>
</template>

<script>
export default {
  props: {
    letters: Array,
    verificarLetra: Function,
    jogar: Function
  }
}
</script>

<style scoped>
  .keyboard-container{
    width: auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    padding: 1rem;
  }
  .keyboard-button {
    margin: 0.25rem;
    width: 3.28125rem;
    border-radius: 0.5rem;
    text-transform: uppercase;
  }
</style>