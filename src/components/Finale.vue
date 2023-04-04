<template>
  <div class="finale-container">
    <div :class="`finale-text ${stage}`">
      {{text}}
    </div>
    <button 
      @click="jogarNovamente"
      class="finale-button"
    >
      Jogar Novamente
    </button>
  </div>
</template>

<script>
export default {
  props: {
    stage: String,
    text: String,
    jogarNovamente: Function
  },
  data(){
    return {

    }
  },
  methods: {
    
  }
}
</script>

<style scoped>
  .finale-text {
    margin: 1.25rem 0;
    font-size: 1.75rem;
    font-weight: bold;
  }
  .finale-text.ganhador {
    color: greenyellow;
  }
  .finale-text.enforcado {
    color: red;
  }
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